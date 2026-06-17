---
id: hello-world
url: annotation/python-net/hello-world
title: Hello, World!
second_title: Basic Example of Using GroupDocs.Annotation for Python via .NET
linkTitle: Hello World
weight: 2
keywords: "hello world, example, get started"
description: Quickly get started with GroupDocs.Annotation for Python via .NET by creating and running a simple example.
productName: GroupDocs.Annotation for Python via .NET
hideChildren: False
toc: True
---

## Introduction
A "Hello, World!" example is often the first step when exploring GroupDocs.Annotation for Python via .NET. It serves as a simple test to confirm that your development environment is correctly set up and that the library is functioning as expected.

## Overview
GroupDocs.Annotation for Python via .NET lets you add annotations, markup, and review comments to a wide range of document and image formats. A wide range of [supported formats](https://docs.groupdocs.com/annotation/python-net/supported-document-formats/) makes it versatile for different use cases.

## How to annotate a document
The following steps demonstrate how to add an annotation to a document using GroupDocs.Annotation for Python via .NET:

1. Import the `groupdocs.annotation` classes you need.
2. Create an annotation and configure it (here, an area annotation with a yellow fill).
3. Open the document with an `Annotator`, pointing it at the sample file.
4. Add the annotation.
5. Save the result.

## Complete example
The example below adds a yellow area (rectangle) annotation to the first page of a PDF and saves the annotated document:

{{< tabs "code-example-hello-world" >}}
{{< tab "hello_world.py" >}}
```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import AreaAnnotation
from groupdocs.pydrawing import Color

def hello_world():
    # Describe a yellow area (rectangle) annotation on the first page
    area = AreaAnnotation()
    area.box = Rectangle(100, 100, 100, 100)          # x, y, width, height
    area.background_color = Color.yellow.to_argb()     # packed ARGB int, not a Color object
    area.page_number = 0                               # page numbers are 0-based
    area.message = "Welcome to GroupDocs.Annotation!"

    # Open the document, add the annotation, and save the result
    with Annotator("./sample.pdf") as annotator:
        annotator.add(area)
        annotator.save("./output.pdf")

    print("Annotation added successfully. Output saved to ./output.pdf.")

if __name__ == "__main__":
    hello_world()
```
{{< /tab >}}
{{< tab "sample.pdf" >}}
{{< tab-text >}}
`sample.pdf` is the sample file used in this example. Click [here](/annotation/python-net/_sample_files/getting-started/hello-world/sample.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "output.pdf" >}}  
```text
Binary file (PDF)
```
[Download full output](/annotation/python-net/_output_files/getting-started/hello-world/hello_world/output.pdf)
{{< /tab >}}
{{< /tabs >}}

This example writes the annotated document to `output.pdf`. Colors are passed as packed ARGB integers (for example `Color.yellow.to_argb()`), not as `Color` objects, and page numbers are 0-based, so `page_number = 0` targets the first page. To annotate a different format, simply open a file with another extension — the same code works across every [supported format](https://docs.groupdocs.com/annotation/python-net/supported-document-formats/).

## Additional resources
This demo references the GroupDocs.Annotation for Python via .NET [code samples](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Python-via-.NET/).
</content>
</invoke>
