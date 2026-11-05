---
id: annotate-pdf-in-csharp
url: annotation/net/annotate-pdf-in-csharp
title: Annotate a PDF in C#
linkTitle: Annotate a PDF
second_title: Highlight, comment, reply and extract with GroupDocs.Annotation for .NET
weight: 2
description: "Add a highlight with a comment and a reply to a PDF in C#, read the markup back out, remove it and render page images - with the page and coordinate rules that decide where the markup lands."
keywords: annotate PDF C#, highlight text PDF C#, add comment to PDF C#, extract annotations from PDF C#, PDF annotation library .NET
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
        name: How to annotate a PDF in C#
        description: Learn how to highlight text in a PDF, attach a comment and a reply, read the markup back and remove it
        steps:
        - name: Install the package
          text: Add the GroupDocs.Annotation package to a .NET project from NuGet.
        - name: Open the document
          text: Create an instance of the Annotator class and pass the file path or a stream.
        - name: Find the text to mark up
          text: Call GetDocumentInfo to read the pages and their text lines with coordinates.
        - name: Add the annotation
          text: Create a HighlightAnnotation with its points, a message and a reply, and pass it to Add.
        - name: Save the result
          text: Call Save with the output path. The markup is written into the document itself.
        - name: Read the markup back
          text: Open the result and call Get to obtain the annotations, their authors and their replies.
---

[GroupDocs.Annotation for .NET](https://products.groupdocs.com/annotation/net/) adds markup to a
document and saves it back in its own format. There is no viewer to embed and no Adobe Acrobat or
Microsoft Office to install: it is a library that reads a file, adds annotations, and writes the
file out again — on Windows, on Linux and in a container.

This page is the shortest complete path through it: open a PDF, highlight a line, attach a comment
with a reply, read the markup back out, remove it, and render page images. The same code runs
unchanged on DOCX, XLSX, PPTX and images — only the file path changes.

{{< alert style="info" >}}
A runnable version of everything on this page is on GitHub:
[annotate-pdf-csharp-net](https://github.com/groupdocs-annotation/annotate-pdf-csharp-net).
Clone it and run `dotnet run --project src/AnnotatePdf -- info samples/quarterly-review.pdf`.
{{< /alert >}}

## Before you start

* .NET 8.0 or later (the library also supports .NET Framework 4.6.2 and .NET 6).
* The package from NuGet:

{{< tabs "install">}}
{{< tab "CLI" >}}
```bash
dotnet add package GroupDocs.Annotation
```
{{< /tab >}}
{{< tab "Package Manager" >}}
```powershell
Install-Package GroupDocs.Annotation
```
{{< /tab >}}
{{< /tabs >}}

Without a licence the library runs in evaluation mode and the output carries evaluation marks.
Apply one at start-up — see [Licensing]({{< ref "annotation/net/getting-started/licensing-and-subscription.md" >}}):

```csharp
new License().SetLicense("GroupDocs.Annotation.lic");
```

## Step 1: open the document

Everything starts with an `Annotator`. It keeps the file open until it is disposed, so wrap it in a
`using` block — and note that it cannot save over the file it is reading. Save to a different path,
or to a temporary file you move into place afterwards.

```csharp
using GroupDocs.Annotation;

using (Annotator annotator = new Annotator("quarterly-review.pdf"))
{
    // add, read or remove markup here
}
```

## Step 2: find the text you want to mark up

Coordinates can be hard-coded, but they rarely survive the next version of the document.
`GetDocumentInfo()` returns every page with its size and its text lines, each with a box, so the
phrase can be located instead of measured:

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Models;

IDocumentInfo info = annotator.Document.GetDocumentInfo();

foreach (PageInfo page in info.PagesInfo)
{
    foreach (TextLineInfo line in page.TextLines)
    {
        if (line.Text.Contains("Hosting costs"))
        {
            // line.LeftIndent, line.TopIndent, line.Width, line.Height - in points, from the TOP-left
        }
    }
}
```

`PageInfo.Width` and `PageInfo.Height` are the page size in points; `TextLineInfo` gives the box of
one line, measured from the **top-left** corner of the page.

## Step 3: add a highlight with a comment and a reply

`HighlightAnnotation.Points` describes one or more rectangles. Four points make one rectangle, in
this order: top-left, top-right, bottom-left, bottom-right. The y values are measured from the
**bottom-left** corner — the convention PDF itself uses — so a line found in step 2 has to be
flipped:

```csharp
using System;
using System.Collections.Generic;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;

float left = (float)line.LeftIndent;
float right = (float)(line.LeftIndent + line.Width);
float top = (float)(page.Height - line.TopIndent);
float bottom = (float)(page.Height - line.TopIndent - line.Height);

HighlightAnnotation highlight = new HighlightAnnotation
{
    PageNumber = page.PageNumber - 1,          // PageInfo is 1-based, annotations are 0-based
    BackgroundColor = 0xFFE699,                // 0xRRGGBB
    Opacity = 0.5,
    Message = "Check this against the invoice",
    CreatedOn = DateTime.Now,
    User = new User { Id = 1, Name = "Reviewer", Role = Role.Editor },
    Points = new List<Point>
    {
        new Point(left, top),
        new Point(right, top),
        new Point(left, bottom),
        new Point(right, bottom)
    },
    Replies = new List<Reply>
    {
        new Reply { Comment = "Confirmed with finance.", RepliedOn = DateTime.Now }
    }
};

annotator.Add(highlight);
```

`Message` is the comment itself. `Replies` starts a thread: in Word the result is a comment with a
reply under it, in a PDF reader it is a note with a response. `User` is what lets a later pass find
and remove exactly this reviewer's markup.

### Page numbers and origins

Three of the four numbers above come from different conventions. Mixing them is the usual reason
markup appears on the wrong page or in the wrong place:

| Member | Origin | Page numbering |
|---|---|---|
| `PageInfo.PageNumber`, `TextLineInfo` | top-left | **1-based** |
| `AnnotationBase.PageNumber` (every annotation type) | — | **0-based** |
| `AreaAnnotation.Box`, `PointAnnotation.Box` | top-left | — |
| `HighlightAnnotation.Points` and other text markup | **bottom-left** | — |
| `PreviewOptions.PageNumbers` | — | **1-based** |

{{< alert style="warning" >}}
An annotation whose `PageNumber` is past the last page is dropped when the document is saved — no
exception is raised and no markup appears. If an annotation "did not show up", check the page index
before anything else.
{{< /alert >}}

## Step 4: save

```csharp
annotator.Save("result.pdf");
```

`Save` writes the markup into the document in its own native form: real PDF annotations in a PDF,
real comments and highlighting in a Word file. Anyone can open the result in Acrobat, in Word or in
a browser without your application.

Pass [SaveOptions](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions)
to write only some annotation types, only annotated pages, or a page range.

## Step 5: read the markup back

```csharp
using (Annotator annotator = new Annotator("result.pdf"))
{
    foreach (AnnotationBase annotation in annotator.Get())
    {
        Console.WriteLine($"#{annotation.Id} {annotation.Type} on page {annotation.PageNumber + 1}");
        Console.WriteLine($"   {annotation.Message} - {annotation.User?.Name}");

        foreach (Reply reply in annotation.Replies)
        {
            Console.WriteLine($"   reply: {reply.Comment}");
        }
    }
}
```

`Get()` reads the annotations the document actually contains, including ones a person added in
Word or Acrobat. `Get(AnnotationType)` narrows the result to one type.

{{< alert style="info" >}}
`Id` is assigned while the document is being read. It is stable for as long as the file does not
change, which is enough to delete or update an annotation in the same session — but it is not a key
to store in a database. To keep annotations outside the document, use
[Export annotations]({{< ref "annotation/net/advanced-usage/export-annotations.md" >}}) and [Import annotations]({{< ref "annotation/net/advanced-usage/import-annotations.md" >}}).
{{< /alert >}}

## Step 6: remove markup

```csharp
using (Annotator annotator = new Annotator("result.pdf"))
{
    annotator.Remove(1);                       // by id
    annotator.Save("clean.pdf");
}
```

To remove one reviewer's markup and leave everyone else's in place, filter by author:

```csharp
List<AnnotationBase> theirs = annotator
    .Get()
    .Where(a => a.User?.Name == "Reviewer")
    .ToList();

annotator.Remove(theirs);
```

## Step 7: render the pages

Page images are what a web front end displays, and what an AI agent looks at to check its own work:

```csharp
using GroupDocs.Annotation.Options;

PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    File.Create($"page_{pageNumber}.png"));

previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.PageNumbers = new[] { 1, 2 };   // 1-based
previewOptions.RenderAnnotations = true;       // false renders the clean page
previewOptions.Resolution = 144;

annotator.Document.GeneratePreview(previewOptions);
```

See [Generate document pages preview]({{< ref "annotation/net/advanced-usage/generate-document-pages-preview.md" >}})
for worksheet columns, resolution and the stream callbacks.

## Running on Linux

Nothing changes in the code. The one thing to remember is fonts: the .NET runtime images ship
without them, and text rendering needs them.

```dockerfile
FROM mcr.microsoft.com/dotnet/runtime:8.0
RUN apt-get update \
 && apt-get install -y --no-install-recommends fontconfig fonts-liberation \
 && rm -rf /var/lib/apt/lists/*
```

A document that uses other fonts needs those fonts installed, or pointed at with
[LoadOptions.FontDirectories]({{< ref "annotation/net/advanced-usage/loading-custom-fonts.md" >}}).

## What to read next

* [Add annotations to the document]({{< ref "annotation/net/annotation-basics/add-annotation-to-the-document/_index.md" >}}) — every annotation type, one page each
* [Working with annotation replies]({{< ref "annotation/net/annotation-basics/working-with-annotation-replies/_index.md" >}}) — review threads
* [Write AI review comments into documents]({{< ref "annotation/net/use-cases/write-ai-review-comments.md" >}}) — the same calls, driven by a model
* [Build an annotation UI for your web app]({{< ref "annotation/net/use-cases/build-annotation-ui-for-web-app.md" >}}) — the same calls, driven from a browser
* Blog: [How to annotate a PDF in C#](https://blog.groupdocs.com/annotation/how-to-annotate-pdf-in-csharp/)
* GitHub: [annotate-pdf-csharp-net](https://github.com/groupdocs-annotation/annotate-pdf-csharp-net)
