---
id: manage-annotations
url: annotation/python-net/manage-annotations
title: Manage annotations
weight: 2
description: "Read every annotation in a document, remove a single annotation by its id, or remove all annotations at once with GroupDocs.Annotation for Python via .NET."
keywords: get annotations, list annotations, remove annotation, remove annotation by id, remove all annotations, python, GroupDocs.Annotation
productName: GroupDocs.Annotation for Python via .NET
hideChildren: False
toc: True
---
Once a document contains annotations you can read them, remove a single one by its id, or remove them all. The [`Annotator`](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation/annotator/) class exposes `get()` to list annotations and `remove(...)` to delete them.

## Get all annotations

Call `get()` to return the list of annotations stored in the document. Each item exposes common properties such as `id`, `message`, `page_number`, and `replies`.

{{< tabs "code-example-get-all-annotations" >}}
{{< tab "get_all_annotations.py" >}}
```python
from groupdocs.annotation import Annotator


def get_all_annotations():
    # Open a document that already contains annotations and list them
    with Annotator("./annotated.pdf") as annotator:
        annotations = annotator.get()
        print(f"Found {len(annotations)} annotation(s):")
        for annotation in annotations:
            print(f"  [{annotation.id}] {type(annotation).__name__}: {annotation.message}")


if __name__ == "__main__":
    get_all_annotations()
```
{{< /tab >}}
{{< tab "annotated.pdf" >}}
{{< tab-text >}}
`annotated.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/manage-annotations/annotated.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

## Remove an annotation by id

Pass the `annotation_id` of the annotation you want to delete to `remove(...)`, then save the document.

{{< tabs "code-example-remove-annotation-by-id" >}}
{{< tab "remove_annotation_by_id.py" >}}
```python
from groupdocs.annotation import Annotator


def remove_annotation_by_id():
    # Open an annotated document and remove a single annotation by its id
    with Annotator("./annotated.pdf") as annotator:
        annotations = annotator.get()
        if annotations:
            annotator.remove(annotation_id=annotations[0].id)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    remove_annotation_by_id()
```
{{< /tab >}}
{{< tab "annotated.pdf" >}}
{{< tab-text >}}
`annotated.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/manage-annotations/annotated.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 90 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/manage-annotations/remove_annotation_by_id/output.pdf)
{{< /tab >}}
{{< /tabs >}}

## Remove all annotations

To clear every annotation, read the list with `get()` and pass it to `remove(...)` through the `annotations_to_delete` parameter.

{{< tabs "code-example-remove-all-annotations" >}}
{{< tab "remove_all_annotations.py" >}}
```python
from groupdocs.annotation import Annotator


def remove_all_annotations():
    # Open an annotated document and remove every annotation
    with Annotator("./annotated.pdf") as annotator:
        annotations = annotator.get()
        if annotations:
            annotator.remove(annotations_to_delete=annotations)
        annotator.save("./output.pdf")


if __name__ == "__main__":
    remove_all_annotations()
```
{{< /tab >}}
{{< tab "annotated.pdf" >}}
{{< tab-text >}}
`annotated.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/developer-guide/basic-usage/manage-annotations/annotated.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF, 88 KB)
```
[Download full output](/annotation/python-net/_output_files/developer-guide/basic-usage/manage-annotations/remove_all_annotations/output.pdf)
{{< /tab >}}
{{< /tabs >}}
