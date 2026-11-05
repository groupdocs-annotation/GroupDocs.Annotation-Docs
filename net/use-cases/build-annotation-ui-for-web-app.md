---
id: build-annotation-ui-for-web-app
url: annotation/net/build-annotation-ui-for-web-app
title: Build an annotation UI for your web app
linkTitle: Browser annotation UI
second_title: Page images, a canvas and four endpoints with ASP.NET Core
weight: 2
description: "GroupDocs.Annotation has no user interface. This page shows how to build one: render page images, draw rectangles on a canvas, map pixels to page coordinates and store the markup in the document through four endpoints."
keywords: document annotation web app C#, annotate PDF in browser ASP.NET Core, build annotation UI, GroupDocs.Annotation web viewer, canvas annotation API
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
        name: How to build a browser annotation UI
        description: Learn how to render document pages, capture rectangles in the browser and store them as annotations
        steps:
        - name: Render the pages
          text: Call GeneratePreview to produce a PNG per page, without annotations, and cache it.
        - name: Publish the page geometry
          text: Return the page count and the size of each page in points so the browser can scale.
        - name: Capture a rectangle
          text: Draw on a canvas over the page image and send the rectangle with the image size it was drawn on.
        - name: Map pixels to page units
          text: Scale the rectangle by page size divided by image size, then add an AreaAnnotation.
        - name: Save by swapping files
          text: Save to a temporary file and move it over the original, because the annotator holds the source open.
        - name: Reload the list
          text: Return the full annotation list after every write so the browser never guesses the state.
---

GroupDocs.Annotation is UI-agnostic: it reads and writes markup inside documents and draws nothing
on a screen. That is the right split for a server library, and it leaves one question for everyone
who adopts it — *how does a person actually draw the annotation?*

This page describes a front end that needs no viewer component, no Angular package and no
third-party PDF renderer: **page images, a canvas, and four endpoints**.

{{< alert style="info" >}}
A runnable implementation — ASP.NET Core minimal API plus about 250 lines of plain JavaScript — is
on GitHub: [browser-annotation-ui-net](https://github.com/groupdocs-annotation/browser-annotation-ui-net).
Clone it, `dotnet run`, and drag a box on the page.
{{< /alert >}}

## The design in one paragraph

The server renders each page once as a PNG **without annotations** and caches it. The browser shows
that image and draws the markup itself, on a canvas on top, from the annotation list the server
returns as data. Adding a comment is a small write to the document plus a reload of the list — not
a re-render of the page. Annotations stay selectable, clickable and answerable instead of being
baked into a picture.

## The endpoints

| Method | Route | Purpose |
|---|---|---|
| `GET` | `/api/documents/{name}/info` | page count and the size of every page, in points |
| `GET` | `/api/documents/{name}/pages/{n}/image` | PNG of page `n` |
| `GET` | `/api/documents/{name}/annotations` | every annotation as one rectangle in page units |
| `POST` | `/api/documents/{name}/annotations` | add one |
| `PUT` | `/api/documents/{name}/annotations/{id}` | change the message or append a reply |
| `DELETE` | `/api/documents/{name}/annotations/{id}` | remove one |

Every write returns the full annotation list, so the browser never has to reason about what the
server now holds.

## Step 1: render the pages

```csharp
using GroupDocs.Annotation;
using GroupDocs.Annotation.Options;

using Annotator annotator = new Annotator(path);

PreviewOptions previewOptions = new PreviewOptions(page => File.Create(CachePath(name, page)))
{
    PreviewFormat = PreviewFormats.PNG,
    PageNumbers = new[] { pageNumber },   // 1-based
    RenderAnnotations = false,            // the canvas draws the markup
    Resolution = 144
};

annotator.Document.GeneratePreview(previewOptions);
```

Cache the result and compare its timestamp against the document's: a page is re-rendered only after
the document actually changes. See
[Generate document pages preview]({{< ref "annotation/net/advanced-usage/generate-document-pages-preview.md" >}})
for resolution, worksheet columns and the stream callbacks.

## Step 2: publish the page geometry

The browser needs the page size to map what it draws back to the document:

```csharp
IDocumentInfo info = annotator.Document.GetDocumentInfo();

var pages = info.PagesInfo
    .Select(page => new { number = page.PageNumber, width = page.Width, height = page.Height })
    .ToList();
```

`PageInfo.Width` and `Height` are in points. `PageInfo.PageNumber` is 1-based.

## Step 3: capture a rectangle in the browser

The canvas sits on top of the image at the same size. On `pointerdown` / `pointermove` /
`pointerup`, keep the rectangle in **image pixels** and send it together with the size of the image
it was drawn on:

```javascript
await fetch(`/api/documents/${name}/annotations`, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        page: currentPage,                  // 1-based
        x, y, width, height,                // pixels on the displayed image
        imageWidth: img.clientWidth,
        imageHeight: img.clientHeight,
        message: window.prompt('Comment'),
        user: 'Reviewer'
    })
});
```

Sending the image size instead of a scale factor is what keeps the UI correct when the preview
resolution changes, when the image is scaled by CSS, or when the page is opened on a phone.

## Step 4: map pixels to page units and store the annotation

```csharp
PageInfo page = info.PagesInfo[request.Page - 1];

double scaleX = page.Width / request.ImageWidth;
double scaleY = page.Height / request.ImageHeight;

annotator.Add(new AreaAnnotation
{
    PageNumber = page.PageNumber - 1,      // PageInfo is 1-based, annotations are 0-based
    Box = new Rectangle(
        (float)(request.X * scaleX),
        (float)(request.Y * scaleY),
        (float)(request.Width * scaleX),
        (float)(request.Height * scaleY)),
    BackgroundColor = 0xFFE699,
    PenColor = 0xE08C00,
    PenWidth = 1,
    Opacity = 0.35,
    CreatedOn = DateTime.Now,
    Message = request.Message,
    User = new User { Id = 1, Name = request.User, Role = Role.Editor }
});
```

`AreaAnnotation.Box` is measured from the **top-left** corner of the page, which is the same
direction the browser measures in — so a box drawn on the canvas maps across with a scale and no
flip.

## Step 5: send one shape of rectangle to the browser

Text markup does not share that origin. `HighlightAnnotation.Points` and the other text-markup types
are measured from the **bottom-left** corner. Convert them on the server, so the front end only ever
sees top-left boxes:

```csharp
if (annotation is AreaAnnotation area)
{
    x = area.Box.X; y = area.Box.Y;
    width = area.Box.Width; height = area.Box.Height;
}
else if (annotation is HighlightAnnotation highlight)
{
    double minX = highlight.Points.Min(p => (double)p.X);
    double maxX = highlight.Points.Max(p => (double)p.X);
    double minY = highlight.Points.Min(p => (double)p.Y);
    double maxY = highlight.Points.Max(p => (double)p.Y);

    x = minX;
    y = page.Height - maxY;                // flip to top-left
    width = maxX - minX;
    height = maxY - minY;
}
```

This is what makes a highlight added in Word, in Acrobat or by a
[machine review pass]({{< ref "annotation/net/use-cases/write-ai-review-comments.md" >}}) appear in
the right place in your UI.

## Step 6: save by swapping files

`Annotator` holds the source file open until it is disposed and cannot save over the file it is
reading. Write next to the original and move the result into place:

```csharp
using (Annotator annotator = new Annotator(path))
{
    annotator.Add(annotation);
    annotator.Save(path + ".tmp");
}

File.Move(path + ".tmp", path, overwrite: true);
InvalidatePreviewCache(name);
```

Take a per-document lock around the whole sequence. Two requests that read, change and rewrite the
same file concurrently will lose one of the changes.

## Replies and updates

```csharp
AnnotationBase annotation = annotator.Get().First(a => a.Id == id);

List<Reply> replies = annotation.Replies?.ToList() ?? new List<Reply>();
replies.Add(new Reply
{
    Comment = text,
    RepliedOn = DateTime.Now,
    User = new User { Id = 2, Name = author, Role = Role.Editor }
});

annotation.Replies = replies;
annotator.Update(annotation);
```

{{< alert style="warning" >}}
`Id` is assigned while the document is read, not stored in it, and it changes after a write. It is
safe to use within one request — read, find, update, save — and it is not a key to hand out. A UI
that reloads the list after every change is fine; a multi-user system should keep annotations in its
own table and use
[Import annotations]({{< ref "annotation/net/advanced-usage/import-annotations.md" >}}) and
[Export annotations]({{< ref "annotation/net/advanced-usage/export-annotations.md" >}}) to move them
in and out of the file.
{{< /alert >}}

## Where to go beyond the sample

* **Text selection.** Use the text lines from
  [GetDocumentInfo]({{< ref "annotation/net/annotation-basics/get-file-info.md" >}}) to let a user
  select words rather than drag a box, and add a `HighlightAnnotation` instead of an area.
* **Large documents.** Render pages on demand and cache them; the sample rewrites the whole document
  on every change, which is fine for a contract and wrong for an archive.
* **Several reviewers.** Set `User` per request and filter by author when rendering, so everyone can
  hide everyone else's markup.
* **A third-party viewer instead.** If you already embed a JavaScript PDF viewer, keep it for
  display and use these endpoints only for storage — the geometry rules above do not change.

## What to read next

* [Annotate a PDF in C#]({{< ref "annotation/net/getting-started/annotate-pdf-in-csharp.md" >}}) — the calls behind the endpoints
* [Generate document pages preview]({{< ref "annotation/net/advanced-usage/generate-document-pages-preview.md" >}}) — rendering options
* [Write AI review comments into documents]({{< ref "annotation/net/use-cases/write-ai-review-comments.md" >}}) — the first pass a person answers in this UI
* Blog: [Build a browser annotation UI on GroupDocs.Annotation](https://blog.groupdocs.com/annotation/build-browser-annotation-ui-aspnet-core/)
* GitHub: [browser-annotation-ui-net](https://github.com/groupdocs-annotation/browser-annotation-ui-net)
