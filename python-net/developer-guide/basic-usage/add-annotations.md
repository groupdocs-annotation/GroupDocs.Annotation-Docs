---
id: add-annotations
url: annotation/python-net/add-annotations
title: Add annotations
weight: 1
description: "Add area, ellipse, point, arrow, distance, polyline, highlight, underline, strikeout, squiggly, text-field, replacement, redaction, watermark, link, and image annotations to a document with GroupDocs.Annotation for Python via .NET."
keywords: add annotations, area annotation, ellipse annotation, watermark annotation, text markup, highlight, underline, strikeout, link annotation, image annotation, python, GroupDocs.Annotation
productName: GroupDocs.Annotation for Python via .NET
hideChildren: False
toc: True
---
GroupDocs.Annotation lets you add many kinds of annotations to PDF, Word, Excel, PowerPoint, image, and other documents. You create an annotation object, set its properties, call [`add`](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation/annotator/) on the [`Annotator`](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation/annotator/), and `save` the result.

A few rules apply to every annotation:

- **Position.** Box-style annotations (area, ellipse, point, arrow, distance, polyline, text field, watermark, resources redaction, image) are positioned with a `Rectangle(x, y, width, height)` assigned to the `.box` property. Text-markup annotations (highlight, underline, strikeout, squiggly, replacement, text redaction, link) are positioned with a list of corner `Point` objects assigned to the `.points` property, in the order top-left, top-right, bottom-left, bottom-right.
- **Colors.** Every color property (`background_color`, `font_color`, `pen_color`, `underline_color`, `squiggly_color`) is a packed **ARGB integer**, not a `Color` object. Use `Color.<name>.to_argb()` or `Color.from_argb(a, r, g, b).to_argb()`.
- **Page index.** `page_number` is **0-based** — `0` is the first page.

## Add an area annotation

An area annotation draws a filled rectangle over a region of the page.

{{< tabs "code-example-add-area-annotation" >}}
{{< tab "add_area_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle, PenStyle
from groupdocs.annotation.models.annotation_models import AreaAnnotation
from groupdocs.pydrawing import Color


def add_area_annotation():
    # Load the document to be annotated
    with Annotator("./sample.pdf") as annotator:
        # Configure an area (rectangle) annotation
        area = AreaAnnotation()
        area.box = Rectangle(100, 100, 100, 100)   # x, y, width, height
        area.background_color = Color.yellow.to_argb()
        area.pen_color = Color.red.to_argb()
        area.pen_width = 3
        area.pen_style = PenStyle.SOLID
        area.opacity = 0.7
        area.page_number = 0
        area.message = "This is an area annotation"

        # Add the annotation and save the result
        annotator.add(area)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_area_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_area_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add an ellipse annotation

An ellipse annotation draws a filled oval inside the bounding box.

{{< tabs "code-example-add-ellipse-annotation" >}}
{{< tab "add_ellipse_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle, PenStyle
from groupdocs.annotation.models.annotation_models import EllipseAnnotation
from groupdocs.pydrawing import Color


def add_ellipse_annotation():
    with Annotator("./sample.pdf") as annotator:
        ellipse = EllipseAnnotation()
        ellipse.box = Rectangle(100, 100, 200, 120)
        ellipse.background_color = Color.from_argb(255, 144, 238, 144).to_argb()
        ellipse.pen_color = Color.green.to_argb()
        ellipse.pen_width = 2
        ellipse.pen_style = PenStyle.SOLID
        ellipse.opacity = 0.7
        ellipse.page_number = 0
        ellipse.message = "This is an ellipse annotation"
        annotator.add(ellipse)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_ellipse_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_ellipse_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a point annotation

A point annotation marks a single location on the page. It is positioned by the origin of its box, so the width and height are `0`.

{{< tabs "code-example-add-point-annotation" >}}
{{< tab "add_point_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import PointAnnotation


def add_point_annotation():
    with Annotator("./sample.pdf") as annotator:
        point = PointAnnotation()
        point.box = Rectangle(100, 100, 0, 0)   # a point is positioned by its box origin
        point.page_number = 0
        point.message = "This is a point annotation"
        annotator.add(point)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_point_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_point_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add an arrow annotation

An arrow annotation draws a directed line across the bounding box.

{{< tabs "code-example-add-arrow-annotation" >}}
{{< tab "add_arrow_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle, PenStyle
from groupdocs.annotation.models.annotation_models import ArrowAnnotation
from groupdocs.pydrawing import Color


def add_arrow_annotation():
    with Annotator("./sample.pdf") as annotator:
        arrow = ArrowAnnotation()
        arrow.box = Rectangle(100, 100, 100, 100)
        arrow.pen_color = Color.blue.to_argb()
        arrow.pen_width = 2
        arrow.pen_style = PenStyle.SOLID
        arrow.opacity = 0.9
        arrow.page_number = 0
        arrow.message = "This is an arrow annotation"
        annotator.add(arrow)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_arrow_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_arrow_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a distance annotation

A distance annotation measures the span between two points on the page.

{{< tabs "code-example-add-distance-annotation" >}}
{{< tab "add_distance_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle, PenStyle
from groupdocs.annotation.models.annotation_models import DistanceAnnotation
from groupdocs.pydrawing import Color


def add_distance_annotation():
    with Annotator("./sample.pdf") as annotator:
        distance = DistanceAnnotation()
        distance.box = Rectangle(100, 100, 100, 100)
        distance.pen_color = Color.blue.to_argb()
        distance.pen_width = 2
        distance.pen_style = PenStyle.SOLID
        distance.opacity = 0.7
        distance.page_number = 0
        distance.message = "This is a distance annotation"
        annotator.add(distance)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_distance_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_distance_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a polyline annotation

A polyline annotation draws a free-form shape described by an SVG path inside the bounding box.

{{< tabs "code-example-add-polyline-annotation" >}}
{{< tab "add_polyline_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle, PenStyle
from groupdocs.annotation.models.annotation_models import PolylineAnnotation
from groupdocs.pydrawing import Color


def add_polyline_annotation():
    with Annotator("./sample.pdf") as annotator:
        polyline = PolylineAnnotation()
        polyline.box = Rectangle(100, 100, 200, 100)
        polyline.svg_path = "M 0 0 L 50 50 L 100 0 L 150 50"
        polyline.pen_color = Color.purple.to_argb()
        polyline.pen_width = 2
        polyline.pen_style = PenStyle.SOLID
        polyline.opacity = 0.9
        polyline.page_number = 0
        polyline.message = "This is a polyline annotation"
        annotator.add(polyline)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_polyline_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_polyline_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a highlight annotation

Highlight, underline, strikeout, and squiggly are text-markup annotations: they are positioned by the corner `Point` objects of the text region rather than a box.

{{< tabs "code-example-add-highlight-annotation" >}}
{{< tab "add_highlight_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Point
from groupdocs.annotation.models.annotation_models import HighlightAnnotation
from groupdocs.pydrawing import Color


def add_highlight_annotation():
    with Annotator("./sample.pdf") as annotator:
        highlight = HighlightAnnotation()
        # Text-markup annotations are positioned by the corner points of the
        # text region: top-left, top-right, bottom-left, bottom-right
        highlight.points = [
            Point(80, 600), Point(300, 600),
            Point(80, 575), Point(300, 575),
        ]
        highlight.background_color = Color.yellow.to_argb()
        highlight.opacity = 0.7
        highlight.page_number = 0
        highlight.message = "This is a highlight annotation"
        annotator.add(highlight)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_highlight_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_highlight_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add an underline annotation

An underline annotation draws a line beneath the selected text region.

{{< tabs "code-example-add-underline-annotation" >}}
{{< tab "add_underline_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Point
from groupdocs.annotation.models.annotation_models import UnderlineAnnotation
from groupdocs.pydrawing import Color


def add_underline_annotation():
    with Annotator("./sample.pdf") as annotator:
        underline = UnderlineAnnotation()
        underline.points = [
            Point(80, 600), Point(300, 600),
            Point(80, 575), Point(300, 575),
        ]
        underline.underline_color = Color.red.to_argb()
        underline.opacity = 0.9
        underline.page_number = 0
        underline.message = "This is an underline annotation"
        annotator.add(underline)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_underline_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_underline_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a strikeout annotation

A strikeout annotation draws a line through the selected text region.

{{< tabs "code-example-add-strikeout-annotation" >}}
{{< tab "add_strikeout_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Point
from groupdocs.annotation.models.annotation_models import StrikeoutAnnotation
from groupdocs.pydrawing import Color


def add_strikeout_annotation():
    with Annotator("./sample.pdf") as annotator:
        strikeout = StrikeoutAnnotation()
        strikeout.points = [
            Point(80, 600), Point(300, 600),
            Point(80, 575), Point(300, 575),
        ]
        strikeout.font_color = Color.red.to_argb()
        strikeout.opacity = 0.9
        strikeout.page_number = 0
        strikeout.message = "This is a strikeout annotation"
        annotator.add(strikeout)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_strikeout_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_strikeout_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a squiggly annotation

A squiggly annotation draws a wavy line under the selected text region.

{{< tabs "code-example-add-squiggly-annotation" >}}
{{< tab "add_squiggly_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Point
from groupdocs.annotation.models.annotation_models import SquigglyAnnotation
from groupdocs.pydrawing import Color


def add_squiggly_annotation():
    with Annotator("./sample.pdf") as annotator:
        squiggly = SquigglyAnnotation()
        squiggly.points = [
            Point(80, 600), Point(300, 600),
            Point(80, 575), Point(300, 575),
        ]
        squiggly.squiggly_color = Color.red.to_argb()
        squiggly.opacity = 0.9
        squiggly.page_number = 0
        squiggly.message = "This is a squiggly annotation"
        annotator.add(squiggly)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_squiggly_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_squiggly_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a text field annotation

A text field annotation places editable text inside a box, with font and alignment control.

{{< tabs "code-example-add-text-field-annotation" >}}
{{< tab "add_text_field_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle, HorizontalAlignment
from groupdocs.annotation.models.annotation_models import TextFieldAnnotation
from groupdocs.pydrawing import Color


def add_text_field_annotation():
    with Annotator("./sample.pdf") as annotator:
        text_field = TextFieldAnnotation()
        text_field.box = Rectangle(100, 100, 150, 50)
        text_field.text = "Some text in a field"
        text_field.font_family = "Arial"
        text_field.font_size = 12.0
        text_field.font_color = Color.black.to_argb()
        text_field.background_color = Color.yellow.to_argb()
        text_field.text_horizontal_alignment = HorizontalAlignment.CENTER
        text_field.opacity = 0.9
        text_field.page_number = 0
        text_field.message = "This is a text field annotation"
        annotator.add(text_field)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_text_field_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_text_field_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a text replacement annotation

A text replacement annotation marks a text region and provides replacement text.

{{< tabs "code-example-add-replacement-annotation" >}}
{{< tab "add_replacement_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Point
from groupdocs.annotation.models.annotation_models import ReplacementAnnotation
from groupdocs.pydrawing import Color


def add_replacement_annotation():
    with Annotator("./sample.pdf") as annotator:
        replacement = ReplacementAnnotation()
        replacement.points = [
            Point(80, 600), Point(300, 600),
            Point(80, 575), Point(300, 575),
        ]
        replacement.text_to_replace = "replacement text"
        replacement.font_color = Color.black.to_argb()
        replacement.font_size = 12.0
        replacement.opacity = 0.9
        replacement.page_number = 0
        replacement.message = "This is a text replacement annotation"
        annotator.add(replacement)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_replacement_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_replacement_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a text redaction annotation

A text redaction annotation hides a text region behind a solid block.

{{< tabs "code-example-add-text-redaction-annotation" >}}
{{< tab "add_text_redaction_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Point
from groupdocs.annotation.models.annotation_models import TextRedactionAnnotation
from groupdocs.pydrawing import Color


def add_text_redaction_annotation():
    with Annotator("./sample.pdf") as annotator:
        redaction = TextRedactionAnnotation()
        redaction.points = [
            Point(80, 600), Point(300, 600),
            Point(80, 575), Point(300, 575),
        ]
        redaction.font_color = Color.black.to_argb()
        redaction.page_number = 0
        redaction.message = "This is a text redaction annotation"
        annotator.add(redaction)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_text_redaction_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_text_redaction_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a resources redaction annotation

A resources redaction annotation blacks out a rectangular region, removing the underlying page resources.

{{< tabs "code-example-add-resources-redaction-annotation" >}}
{{< tab "add_resources_redaction_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import ResourcesRedactionAnnotation


def add_resources_redaction_annotation():
    with Annotator("./sample.pdf") as annotator:
        redaction = ResourcesRedactionAnnotation()
        redaction.box = Rectangle(100, 100, 200, 80)
        redaction.page_number = 0
        redaction.message = "This is a resources redaction annotation"
        annotator.add(redaction)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_resources_redaction_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_resources_redaction_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a watermark annotation

A watermark annotation places rotated, scalable text over the page.

{{< tabs "code-example-add-watermark-annotation" >}}
{{< tab "add_watermark_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle, HorizontalAlignment, VerticalAlignment
from groupdocs.annotation.models.annotation_models import WatermarkAnnotation
from groupdocs.pydrawing import Color


def add_watermark_annotation():
    with Annotator("./sample.pdf") as annotator:
        watermark = WatermarkAnnotation()
        watermark.box = Rectangle(100, 100, 200, 100)
        watermark.text = "Watermark"
        watermark.font_family = "Arial"
        watermark.font_size = 24.0
        watermark.font_color = Color.red.to_argb()
        watermark.angle = 45.0
        watermark.auto_scale = True
        watermark.horizontal_alignment = HorizontalAlignment.CENTER
        watermark.vertical_alignment = VerticalAlignment.CENTER
        watermark.opacity = 0.5
        watermark.page_number = 0
        watermark.message = "This is a watermark annotation"
        annotator.add(watermark)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_watermark_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_watermark_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add a link annotation

A link annotation turns a text region into a clickable hyperlink.

{{< tabs "code-example-add-link-annotation" >}}
{{< tab "add_link_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Point
from groupdocs.annotation.models.annotation_models import LinkAnnotation
from groupdocs.pydrawing import Color


def add_link_annotation():
    with Annotator("./sample.pdf") as annotator:
        link = LinkAnnotation()
        link.points = [
            Point(80, 600), Point(300, 600),
            Point(80, 575), Point(300, 575),
        ]
        link.url = "https://www.groupdocs.com"
        link.background_color = Color.azure.to_argb()
        link.opacity = 0.7
        link.page_number = 0
        link.message = "This is a link annotation"
        annotator.add(link)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_link_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_link_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Add an image annotation

An image annotation stamps a picture from disk onto the page. Set `image_path` to a local image file.

{{< tabs "code-example-add-image-annotation" >}}
{{< tab "add_image_annotation.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import ImageAnnotation


def add_image_annotation():
    with Annotator("./sample.pdf") as annotator:
        image = ImageAnnotation()
        image.box = Rectangle(100, 100, 100, 100)
        image.image_path = "./stamp.png"
        image.opacity = 0.9
        image.angle = 0.0
        image.page_number = 0
        image.message = "This is an image annotation"
        annotator.add(image)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    add_image_annotation()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the document used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "stamp.png" >}}
{{< tab-text >}}
`stamp.png` is the image stamped onto the page. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/add-annotations/stamp.png) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 95 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/add-annotations/add_image_annotation/output.pdf)
{{< /tab >}}
{{< /tabs >}}
