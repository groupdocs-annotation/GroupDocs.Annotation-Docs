---
id: write-ai-review-comments
url: annotation/net/write-ai-review-comments
title: Write AI review comments into documents
linkTitle: AI review comments
second_title: Turn a model's findings into highlights and reply threads with C#
weight: 1
description: "Take the {quote, comment} findings a language model returns, locate each quote on the page and write it into the document as a highlight with a comment and a reply thread - in PDF, Word, Excel and PowerPoint, server-side, with no Word add-in."
keywords: AI document review C#, LLM add comments to Word document, AI redline PDF API, write AI findings as annotations, agent document review .NET
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
structuredData:
    showOrganization: True
    application:
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to write AI review comments into a document
        description: Learn how to anchor a language model's findings on the page and save them as annotations with reply threads
        steps:
        - name: Ask the model for findings
          text: Prompt the model to return a JSON array of objects with a verbatim quote, a comment and a severity.
        - name: Read the page text
          text: Call GetDocumentInfo to obtain every page with its size and its text lines with coordinates.
        - name: Locate each quote
          text: Match the quote against a single text line, or against a run of consecutive lines when it wraps.
        - name: Convert the coordinates
          text: Flip the top-based line box to the bottom-based origin used by text markup and subtract one from the page number.
        - name: Add the annotation
          text: Create a HighlightAnnotation with the message, the author and a reply, and pass it to Add.
        - name: Save and review
          text: Save the document. The remarks open as comments with replies in Word and in any PDF reader.
---

A model that reviews a contract answers in a chat window. The colleague who opens the contract next
week sees none of it. This page is about the other half: taking what the model found and writing it
**into the file**, as a highlight on the sentence it quoted, with its remark as the comment and a
reply thread a person can answer.

[GroupDocs.Annotation for .NET](https://products.groupdocs.com/annotation/net/) does that
server-side, with no Word add-in and no browser extension, and the same code path covers **PDF,
DOCX, XLSX and PPTX**.

{{< alert style="info" >}}
A runnable implementation of this page is on GitHub:
[ai-document-review-annotations-net](https://github.com/groupdocs-annotation/ai-document-review-annotations-net).
It reads findings from a JSON file, or asks a model for them, and writes them into the document.
{{< /alert >}}

## The contract between the model and the document

Keep it small. Everything this design needs from a model is a list of objects with three fields:

```json
[
  {
    "quote": "pay all invoices within ninety days",
    "comment": "Ninety-day payment terms are three times our standard. Ask for thirty days.",
    "severity": "high"
  }
]
```

`quote` is the anchor: it has to be **copied verbatim** from the document, because the next step
searches for it on the page. Ask for 4 to 15 words — long enough to be unique, short enough that it
does not wrap across half a page. `comment` becomes the annotation's message, `severity` picks the
colour.

The model never sees the file format and never produces coordinates. That is what keeps the same
prompt working for a PDF, a Word file and a spreadsheet.

## Step 1: read the page text with its geometry

`GetDocumentInfo()` returns the pages, their size, and the text lines on each with a box per line:

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;

using Annotator annotator = new Annotator("service-agreement.docx");
IDocumentInfo info = annotator.Document.GetDocumentInfo();

foreach (PageInfo page in info.PagesInfo)
{
    foreach (TextLineInfo line in page.TextLines)
    {
        // line.Text, line.LeftIndent, line.TopIndent, line.Width, line.Height
    }
}
```

The same call also produces the plain text to send to the model — page by page, so the answer can
be checked against the page it came from.

## Step 2: match the quote to lines

A model quotes the sentence it read. The page shows that sentence broken across two or three lines.
Matching has to allow for that:

1. look for a single line whose text contains the quote;
2. otherwise join consecutive lines and look for the quote in that window — then mark each line the
   quote covers;
3. otherwise report the finding as unanchored. Never place it at a guess.

Normalise before comparing: collapse runs of whitespace, and fold curly quotes, en dashes and
non-breaking spaces to their plain equivalents. Models reproduce text with a tidier typography than
the document has.

Within a line, the horizontal offset can be estimated from the character position:

```csharp
double perChar = line.Width / normalisedLineText.Length;
double x = line.LeftIndent + (perChar * offsetOfQuoteInLine);
double width = perChar * quoteLength;
```

That assumes an even character width. It is approximate, and it never moves the highlight off the
line — which is the only property that matters here.

## Step 3: convert the coordinates

Three conventions meet in this step:

| Member | Origin | Page numbering |
|---|---|---|
| `PageInfo.PageNumber`, `TextLineInfo` | top-left | **1-based** |
| `AnnotationBase.PageNumber` | — | **0-based** |
| `HighlightAnnotation.Points` and other text markup | **bottom-left** | — |
| `AreaAnnotation.Box` | top-left | — |

So a line at `TopIndent = t` with height `h` on a page of height `H` spans `H - t - h` … `H - t`,
and the page index is `PageInfo.PageNumber - 1`.

{{< alert style="warning" >}}
Passing `PageInfo.PageNumber` straight into `AnnotationBase.PageNumber` puts every annotation one
page too far — and the ones meant for the last page vanish, because an annotation addressed to a
page that does not exist is dropped when the document is saved, with no exception.
{{< /alert >}}

## Step 4: write the annotation

```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

User reviewer = new User { Id = 1, Name = "AI reviewer", Role = Role.Editor };

float left = (float)box.X;
float right = (float)(box.X + box.Width);
float top = (float)(page.Height - box.Y);
float bottom = (float)(page.Height - box.Y - box.Height);

annotator.Add(new HighlightAnnotation
{
    PageNumber = page.PageNumber - 1,
    BackgroundColor = 0xFFE699,            // amber for "medium"
    Opacity = 0.5,
    Message = finding.Comment,
    CreatedOn = DateTime.Now,
    User = reviewer,
    Points = new List<Point>
    {
        new Point(left, top),
        new Point(right, top),
        new Point(left, bottom),
        new Point(right, bottom)
    },
    Replies = new List<Reply>
    {
        new Reply
        {
            Comment = $"Severity: {finding.Severity}. Reply to accept or reject this remark.",
            RepliedOn = DateTime.Now,
            User = reviewer
        }
    }
});

annotator.Save("service-agreement.reviewed.docx");
```

Two details worth copying:

* **Do not repeat the message in the reply.** Word renders both, so the same sentence would appear
  twice in the margin. Use the reply to open the thread — the severity, what to do with the remark —
  and let the message carry the finding.
* **A quote that wraps needs several rectangles in one annotation.** `Points` is a flat list: four
  points per rectangle, in the order top-left, top-right, bottom-left, bottom-right. One
  `HighlightAnnotation` can therefore cover three lines and still be one comment.

### Colours

`BackgroundColor` is `0xRRGGBB`. A PDF keeps the exact value. Word has a fixed palette of highlight
colours and snaps to the nearest one, so a pale amber comes out as yellow there. Pick severities
that stay distinguishable after snapping — for example amber, red and light blue.

## Step 5: let a human answer, and let the review be withdrawn

Because every annotation carries `User.Name`, the machine-written pass can be removed later without
touching anything a person added:

```csharp
using (Annotator annotator = new Annotator("service-agreement.reviewed.docx"))
{
    List<AnnotationBase> machineWritten = annotator
        .Get()
        .Where(a => a.User?.Name == "AI reviewer")
        .ToList();

    annotator.Remove(machineWritten);
    annotator.Save("service-agreement.clean.docx");
}
```

That is what makes the whole approach safe to try on real documents: the review is a layer, not an
edit. Replies people add live in the same thread and are read back with
[Get]({{< ref "annotation/net/annotation-basics/extract-annotations-from-document.md" >}}), so a
second pass can see what was accepted.

## Checking the result

Render the annotated pages and look at them — the cheapest possible test, and the one that catches a
coordinate mistake immediately:

```csharp
PreviewOptions previewOptions = new PreviewOptions(pageNumber => File.Create($"page_{pageNumber}.png"));
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.RenderAnnotations = true;
annotator.Document.GeneratePreview(previewOptions);
```

In a test suite, assert on three things: the number of annotations written, the number of findings
that could not be anchored, and that every `PageNumber` is within the page count.

## What to read next

* [Annotate a PDF in C#]({{< ref "annotation/net/getting-started/annotate-pdf-in-csharp.md" >}}) — the calls used here, one at a time
* [Working with annotation replies]({{< ref "annotation/net/annotation-basics/working-with-annotation-replies/_index.md" >}}) — threads and authors
* [Build an annotation UI for your web app]({{< ref "annotation/net/use-cases/build-annotation-ui-for-web-app.md" >}}) — where a person answers the machine's remarks
* [Annotate documents with AI agents over MCP]({{< ref "annotation/mcp/use-cases/annotate-documents-with-ai-agents.md" >}}) — the same idea driven from a chat client instead of your own code
* Blog: [Let an LLM review a contract and leave real comments in PDF and Word](https://blog.groupdocs.com/annotation/ai-review-comments-pdf-word-csharp/)
* GitHub: [ai-document-review-annotations-net](https://github.com/groupdocs-annotation/ai-document-review-annotations-net)
