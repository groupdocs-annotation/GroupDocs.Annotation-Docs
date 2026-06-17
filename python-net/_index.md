---
id: home
url: annotation/python-net
title: GroupDocs.Annotation for Python via .NET
weight: 1
description: "Native Python library that adds, edits, and removes annotations and markup — area and shape annotations, text highlight/underline/strikeout, watermarks, image and link stamps, and threaded comments — on PDF, Word, Excel, PowerPoint, images, CAD, Visio, and email files on Windows, Linux, and macOS. No Microsoft Office or Adobe Acrobat required."
keywords: GroupDocs.Annotation, Python via .NET, document annotation, annotate PDF, annotate DOCX, markup, comments, replies, highlight, underline, strikeout, watermark, image annotation, link annotation, on-premise, Windows, Linux, macOS
productName: GroupDocs.Annotation for Python via .NET
hideChildren: true
toc: True
structuredData:
    showOrganization: true
---

<img src="/logo/128x128/groupdocs-annotation-python.png" alt="groupdocs-annotation-python-home" align="left" style="width:110px; margin: 0 30px 30px 0"/>

<img src="https://img.shields.io/pypi/v/groupdocs-annotation-net?label=GroupDocs.Annotation%20PyPI" alt="PyPI package">
<img src="https://img.shields.io/pypi/dm/groupdocs-annotation-net?label=pypi%20downloads" alt="PyPI downloads">

{{< button style="primary" link="https://releases.groupdocs.com/annotation/python-net/release-notes/" >}} <svg class="gdoc-icon gdoc-product-doc__btn-icon"><use xlink:href="/img/groupdocs-stack.svg#document"></use></svg> Release notes {{< /button >}}
{{< button style="primary" link="https://pypi.org/project/groupdocs-annotation-net/" >}} {{< icon "gdoc_download" >}} Download from PyPI {{< /button >}}
{{< button style="primary" link="https://products.groupdocs.app/annotation/family" >}} <svg class="gdoc-icon gdoc-product-doc__btn-icon"><use xlink:href="/img/groupdocs-stack.svg#app"></use></svg> Online app {{< /button >}}

[GroupDocs.Annotation for Python via .NET](https://products.groupdocs.com/annotation/python-net/) is a document annotation API that adds, edits, and removes annotations and markup across many document formats. It provides a unified, format-independent interface to draw area and shape annotations, mark up text with highlights, underlines, strikeouts, and squiggly lines, stamp watermarks, images, and hyperlinks, add editable text fields, and attach threaded review comments — then save the result back to its original format with optional page-range and annotation-type filters.

<div style="clear:left"></div>

## Quick example

```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import AreaAnnotation
from groupdocs.pydrawing import Color

# Add an area annotation to the first page of a PDF
with Annotator("input.pdf") as annotator:
    area = AreaAnnotation()
    area.box = Rectangle(100, 100, 200, 80)        # x, y, width, height
    area.page_number = 0                            # 0-based page index
    area.background_color = Color.yellow.to_argb()  # ARGB int, not a Color object
    area.message = "Review this section"
    annotator.add(area)
    annotator.save("annotated.pdf")
```

## Features

- **Shape Annotations**: Draw area, ellipse, arrow, point, distance, and polyline annotations with configurable color and opacity.
- **Text Markup**: Highlight, underline, strikeout, and squiggly-mark text, replace or redact text, and redact embedded resources.
- **Content Annotations**: Stamp watermarks, image annotations, hyperlinks, and editable text fields onto a document.
- **Comments & Replies**: Attach threaded review comments to any annotation with user and timestamp information.
- **Manage Annotations**: List, update, and remove annotations — all of them or filtered by annotation type.
- **Save Filters**: Render only selected annotation types or a specific page range when saving the result.

## Supported File Formats

GroupDocs.Annotation supports a wide range of file formats. For a complete list, see the [full list of supported formats](https://docs.groupdocs.com/annotation/python-net/getting-started/supported-document-formats/).

- **Microsoft Office** (Word, Excel, PowerPoint)
- **PDF**
- **Images** (JPEG, PNG, BMP, TIFF)
- **CAD** (DWG, DXF)
- **Visio Diagrams** (VSD, VSDX)
- **Email** (EML, EMLX)
- **OpenDocument** (ODT, ODS, ODP)

## Getting Started

To get started, refer to the [System Requirements](https://docs.groupdocs.com/annotation/python-net/getting-started/system-requirements/), [Supported File Formats](https://docs.groupdocs.com/annotation/python-net/getting-started/supported-document-formats/), [Installation](https://docs.groupdocs.com/annotation/python-net/getting-started/installation/), and [Hello, World!](https://docs.groupdocs.com/annotation/python-net/getting-started/hello-world/) sections for setup instructions and your first annotation.

## Developer Guide

For practical, runnable code examples covering basic and advanced annotation, see the [Developer Guide](https://docs.groupdocs.com/annotation/python-net/developer-guide/) section. It walks through loading documents, adding every annotation type, attaching comments and replies, listing and removing annotations, and saving results with page-range and annotation-type filters.

## AI Agents & LLM Integration

Using an AI coding assistant? The [AI Agents & LLM Integration]({{< ref "annotation/python-net/agents-and-llm-integration.md" >}}) page covers the bundled `AGENTS.md` reference, the GroupDocs MCP server, and machine-readable documentation.

## Technical Support

If you experience any issues or have suggestions, see [Technical Support]({{< ref "annotation/python-net/technical-support.md" >}}) for the available channels — the free support forum and the paid helpdesk. For licensing and evaluation questions, see [Licensing and Subscription](https://docs.groupdocs.com/annotation/python-net/getting-started/licensing-and-subscription/).
