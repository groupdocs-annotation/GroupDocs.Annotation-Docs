---
id: saving-documents
url: annotation/python-net/saving-documents
title: Saving documents
linkTitle: Saving documents
weight: 2
description: "Save annotated documents with GroupDocs.Annotation for Python via .NET — persist only specific annotation types or limit the output to a page range with SaveOptions."
keywords: save document, save options, annotation types, page range, first page, last page, python, GroupDocs.Annotation
productName: GroupDocs.Annotation for Python via .NET
hideChildren: False
toc: True
---
By default `save()` writes every annotation back into the document. With [`SaveOptions`](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation.options/saveoptions/) you can persist only certain annotation types or limit the output to a range of pages. Pass the configured `SaveOptions` to `save()` through the `save_options` parameter.

## Save specific annotation types

Set `annotation_types` to an [`AnnotationType`](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation.options/annotationtype/) value to write only annotations of that type, even if the document contains others.

{{< tabs "code-example-save-specific-annotation-types" >}}
{{< tab "save_specific_annotation_types.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import AreaAnnotation, EllipseAnnotation
from groupdocs.annotation.options import SaveOptions, AnnotationType
from groupdocs.pydrawing import Color


def save_specific_annotation_types():
    with Annotator("./sample.pdf") as annotator:
        area = AreaAnnotation()
        area.box = Rectangle(100, 100, 100, 100)
        area.background_color = Color.yellow.to_argb()
        area.page_number = 0
        area.message = "Area"

        ellipse = EllipseAnnotation()
        ellipse.box = Rectangle(100, 250, 150, 80)
        ellipse.background_color = Color.from_argb(255, 144, 238, 144).to_argb()
        ellipse.page_number = 0
        ellipse.message = "Ellipse"

        annotator.add(area)
        annotator.add(ellipse)

        # Persist only the area annotations
        save_options = SaveOptions()
        save_options.annotation_types = AnnotationType.AREA
        annotator.save("./output.pdf", save_options=save_options)


if __name__ == "__main__":
    save_specific_annotation_types()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/advanced-usage/saving-documents/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/advanced-usage/saving-documents/save_specific_annotation_types/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Save a page range

Set `first_page` and `last_page` to write only a range of pages. These values are **1-based** — page `1` is the first page.

{{< tabs "code-example-save-specific-pages" >}}
{{< tab "save_specific_pages.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import AreaAnnotation
from groupdocs.annotation.options import SaveOptions
from groupdocs.pydrawing import Color


def save_specific_pages():
    with Annotator("./multipage_sample.pdf") as annotator:
        area = AreaAnnotation()
        area.box = Rectangle(100, 100, 100, 100)
        area.background_color = Color.yellow.to_argb()
        area.page_number = 0
        area.message = "Page 1 annotation"
        annotator.add(area)

        # first_page / last_page are 1-based for SaveOptions
        save_options = SaveOptions()
        save_options.first_page = 1
        save_options.last_page = 2
        annotator.save("./output.pdf", save_options=save_options)


if __name__ == "__main__":
    save_specific_pages()
```
{{< /tab >}}
{{< tab "multipage_sample.pdf" >}}
{{< tab-text >}}
`multipage_sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/advanced-usage/saving-documents/multipage_sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 92 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/advanced-usage/saving-documents/save_specific_pages/output.pdf)
{{< /tab >}}
{{< /tabs >}}
