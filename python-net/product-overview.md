---
id: product-overview
url: annotation/python-net/product-overview
title: GroupDocs.Annotation for Python via .NET Overview
linkTitle: Product overview
weight: 1
description: "GroupDocs.Annotation for Python via .NET adds, edits, and removes annotations and markup — area and shape annotations, text highlight/underline/strikeout, watermarks, image and link stamps, and threaded comments — on PDF, DOCX, XLSX, PPTX, images, CAD, Visio, and email files, entirely on-premise without Microsoft Office."
keywords: annotation, annotate, markup, comments, replies, PDF, DOCX, XLSX, PPTX, images, CAD, Visio, email, highlight, underline, strikeout, watermark, link, area annotation, python, on-premise
productName: GroupDocs.Annotation for Python via .NET
toc: True
aliases:
  - /annotation/python-net/groupdocs.annotation-overview/
  - /annotation/python-net/groupdocs-annotation-overview/
---

## What is GroupDocs.Annotation?

GroupDocs.Annotation for Python via .NET is a native Python library that **adds, edits, and removes annotations and markup** on documents — across PDF, Microsoft Word, Excel, PowerPoint, images, CAD, Visio, and email formats — through a single, format-independent API. It runs entirely on-premise, requires no Microsoft Office or Adobe Acrobat installation, and ships as a pre-built wheel on Windows, Linux, and macOS.

Typical uses include:

- **Document review & collaboration** — add area, shape, and text-markup annotations and attach threaded reviewer comments so teams can discuss a document in place.
- **Legal & contract markup** — highlight clauses, strike out obsolete text, and flag regions that need attention before a document is signed or shared.
- **Engineering & design review** — annotate CAD drawings and Visio diagrams with area, arrow, and distance markups.
- **Content & e-learning feedback** — mark up images and scanned pages with points, watermarks, and image stamps.
- **Automated annotation pipelines** — stamp watermarks, links, and notes across many documents and save only the annotation types or page ranges you need.

## Key Capabilities

| Capability | Description |
|---|---|
| **Shape Annotations** | Draw area, ellipse, arrow, point, distance, and polyline annotations with configurable color and opacity. |
| **Text Markup** | Highlight, underline, strikeout, and squiggly-mark text, plus replacement, text-redaction, and resources-redaction annotations. |
| **Content Annotations** | Stamp watermarks, image annotations, hyperlinks, and editable text fields onto a document. |
| **Comments & Replies** | Attach threaded review comments — with user and timestamp — to any annotation. |
| **Manage Annotations** | List, update, and remove annotations, all of them or filtered by annotation type. |
| **Save Filters** | Render only selected annotation types, or a specific page range, when saving the result. |
| **Document Inspection** | Read file type, page count, and size without modifying the document. |

Every capability is covered with runnable, copy-paste examples in the [Developer Guide](https://docs.groupdocs.com/annotation/python-net/developer-guide/).

## Quick Example

Add an annotation and save the result with just a few lines of code. The example draws a yellow area annotation on the first page of `sample.pdf` and writes the result to `annotated.pdf`:

{{< tabs "product-overview-add-area" >}}
{{< tab "annotate_area.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import AreaAnnotation
from groupdocs.pydrawing import Color

def annotate_area():
    # Open the document
    with Annotator("./sample.pdf") as annotator:
        # Build an area annotation on the first page
        area = AreaAnnotation()
        area.box = Rectangle(100, 100, 200, 80)        # x, y, width, height
        area.page_number = 0                            # 0-based page index
        area.background_color = Color.yellow.to_argb()  # ARGB int, not a Color object
        area.message = "Review this section"
        annotator.add(area)
        # Save the annotated document
        annotator.save("./annotated.pdf")

if __name__ == "__main__":
    annotate_area()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/product-overview/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "annotated.pdf" >}}  
```text
Binary file (PDF, 1.0 MB)
```
[Download full output](/annotation/python-net/_output_files/product-overview/annotate_area/annotated.pdf)
{{< /tab >}}
{{< /tabs >}}

For richer review workflows, add several annotations, attach a comment thread, and save only the area annotations with a page-range filter using `SaveOptions`:

{{< tabs "product-overview-add-options" >}}
{{< tab "annotate_with_options.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle, Point, Reply
from groupdocs.annotation.models.annotation_models import AreaAnnotation, HighlightAnnotation
from groupdocs.annotation.options import SaveOptions, AnnotationType
from groupdocs.pydrawing import Color

def annotate_with_options():
    with Annotator("./sample.pdf") as annotator:
        # An area annotation carrying a threaded review comment
        area = AreaAnnotation()
        area.box = Rectangle(100, 100, 200, 80)
        area.page_number = 0
        area.background_color = Color.yellow.to_argb()
        area.message = "Please review"
        reply = Reply()
        reply.comment = "Confirmed, looks good"
        area.replies = [reply]

        # A text highlight described by a quad of points
        highlight = HighlightAnnotation()
        highlight.page_number = 0
        highlight.font_color = Color.lime.to_argb()
        highlight.points = [Point(80, 730), Point(240, 730), Point(240, 750), Point(80, 750)]

        annotator.add([area, highlight])

        # Render only area annotations, and only the first page
        options = SaveOptions()
        options.annotation_types = AnnotationType.AREA
        options.first_page = 1      # SaveOptions pages are 1-based
        options.last_page = 1
        annotator.save("./annotated.pdf", save_options=options)

if __name__ == "__main__":
    annotate_with_options()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/product-overview/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "annotated.pdf" >}}  
```text
Binary file (PDF, 1.0 MB)
```
[Download full output](/annotation/python-net/_output_files/product-overview/annotate_with_options/annotated.pdf)
{{< /tab >}}
{{< /tabs >}}

## Where to next

1. **Install the package** — [Installation](https://docs.groupdocs.com/annotation/python-net/getting-started/installation/) walks through PyPI and offline wheel installation for Windows, Linux, and macOS.
2. **Run your first annotation** — [Hello, World!](https://docs.groupdocs.com/annotation/python-net/getting-started/hello-world/) annotates a document in under five minutes.
3. **Explore runnable examples** — [How to Run Examples](https://docs.groupdocs.com/annotation/python-net/getting-started/how-to-run-examples/) clones the GitHub repository and runs every documented scenario locally or in Docker.
4. **Use it in depth** — the [Developer Guide](https://docs.groupdocs.com/annotation/python-net/developer-guide/) covers every API surface with runnable, copy-paste code examples.
5. **Plug it into AI pipelines** — [AI Agents & LLM Integration]({{< ref "annotation/python-net/agents-and-llm-integration.md" >}}) explains the bundled `AGENTS.md`, the MCP server, and machine-readable docs.
</content>
