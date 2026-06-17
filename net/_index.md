---
id: home
url: annotation/net
title: GroupDocs.Annotation for .NET
weight: 1
description: ".NET library that adds, edits, and removes annotations and markup — area and shape annotations, text highlight/underline/strikeout, watermarks, image and link stamps, and threaded comments — on PDF, Word, Excel, PowerPoint, images, CAD, Visio, and email files. No Microsoft Office or Adobe Acrobat required."
keywords: GroupDocs.Annotation, .NET, C#, document annotation, annotate PDF, annotate DOCX, markup, comments, replies, highlight, underline, strikeout, watermark, image annotation, link annotation, on-premise
productName: GroupDocs.Annotation for .NET
hideChildren: true
toc: True
structuredData:
    showOrganization: true
---

<img src="/logo/128x128/groupdocs-annotation-net.png" alt="groupdocs-annotation-net-home" align="left" style="width:110px; margin: 0 30px 30px 0"/>

<img src="https://img.shields.io/nuget/v/GroupDocs.Annotation?label=GroupDocs.Annotation%20NuGet" alt="NuGet package">
<img src="https://img.shields.io/nuget/dt/GroupDocs.Annotation?label=nuget%20downloads" alt="NuGet downloads">

{{< button style="primary" link="https://releases.groupdocs.com/annotation/net/release-notes/" >}} <svg class="gdoc-icon gdoc-product-doc__btn-icon"><use xlink:href="/img/groupdocs-stack.svg#document"></use></svg> Release notes {{< /button >}}
{{< button style="primary" link="https://www.nuget.org/packages/GroupDocs.Annotation/" >}} {{< icon "gdoc_download" >}} Download from NuGet {{< /button >}}
{{< button style="primary" link="https://products.groupdocs.app/annotation/family" >}} <svg class="gdoc-icon gdoc-product-doc__btn-icon"><use xlink:href="/img/groupdocs-stack.svg#app"></use></svg> Online app {{< /button >}}

[GroupDocs.Annotation for .NET](https://products.groupdocs.com/annotation/net/) is a document annotation API that adds, edits, and removes annotations and markup across many document formats. It provides a unified, format-independent interface to draw area and shape annotations, mark up text with highlights, underlines, strikeouts, and squiggly lines, stamp watermarks, images, and hyperlinks, add editable text fields, and attach threaded review comments — then save the result back to its original format with optional page-range and annotation-type filters.

<div style="clear:left"></div>

## Quick example

```csharp
// Add an area annotation to the first page of a PDF
using (Annotator annotator = new Annotator("input.pdf"))
{
    AreaAnnotation area = new AreaAnnotation
    {
        Box = new Rectangle(100, 100, 200, 80),   // x, y, width, height
        PageNumber = 0,                            // 0-based page index
        BackgroundColor = 65535,                   // ARGB integer
        Message = "Review this section"
    };
    annotator.Add(area);
    annotator.Save("annotated.pdf");
}
```

## Features

- **Shape Annotations**: Draw area, ellipse, arrow, point, distance, and polyline annotations with configurable color and opacity.
- **Text Markup**: Highlight, underline, strikeout, and squiggly-mark text, replace or redact text, and redact embedded resources.
- **Content Annotations**: Stamp watermarks, image annotations, hyperlinks, and editable text fields onto a document.
- **Comments & Replies**: Attach threaded review comments to any annotation with user and timestamp information.
- **Manage Annotations**: List, update, and remove annotations — all of them or filtered by annotation type.
- **Save Filters**: Render only selected annotation types or a specific page range when saving the result.

## Supported File Formats

GroupDocs.Annotation supports a wide range of file formats. For a complete list, see the [full list of supported formats](https://docs.groupdocs.com/annotation/net/getting-started/supported-document-formats/).

- **Microsoft Office** (Word, Excel, PowerPoint)
- **PDF**
- **Images** (JPEG, PNG, BMP, TIFF)
- **CAD** (DWG, DXF)
- **Visio Diagrams** (VSD, VSDX)
- **Email** (EML, EMLX)
- **OpenDocument** (ODT, ODS, ODP)

## Getting Started

To get started, refer to the [System Requirements](https://docs.groupdocs.com/annotation/net/getting-started/system-requirements/), [Supported File Formats](https://docs.groupdocs.com/annotation/net/getting-started/supported-document-formats/), [Installation](https://docs.groupdocs.com/annotation/net/getting-started/installation/), and [How to Run Examples](https://docs.groupdocs.com/annotation/net/getting-started/how-to-run-examples/) sections for setup instructions and your first annotation.

## Developer Guide

For practical code examples covering basic and advanced annotation, see the [Basic Usage](https://docs.groupdocs.com/annotation/net/basic-usage/) and [Advanced Usage](https://docs.groupdocs.com/annotation/net/advanced-usage/) sections. They walk through loading documents, adding every annotation type, attaching comments and replies, listing and removing annotations, and saving results with page-range and annotation-type filters.

## Technical Support

If you experience any issues or have suggestions, use the [GroupDocs Free Support Forum](https://forum.groupdocs.com/c/annotation/) or the [Paid Support Helpdesk](https://helpdesk.groupdocs.com/). For licensing and evaluation questions, see [Licensing and Subscription](https://docs.groupdocs.com/annotation/net/getting-started/licensing-and-subscription/).
