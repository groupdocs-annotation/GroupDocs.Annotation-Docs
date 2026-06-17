---
id: generate-document-preview
url: annotation/python-net/generate-document-preview
title: Generate document preview
linkTitle: Generate document preview
weight: 3
description: "Render document pages to preview images with GroupDocs.Annotation for Python via .NET using PreviewOptions and page-stream callbacks."
keywords: document preview, render pages, page preview, PreviewOptions, PreviewFormats, create page stream, python, GroupDocs.Annotation
productName: GroupDocs.Annotation for Python via .NET
hideChildren: False
toc: True
---
Use [`Document.generate_preview`](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation/document/) to render document pages to image files (PNG, JPEG, or BMP). You configure the render with [`PreviewOptions`](https://reference.groupdocs.com/annotation/python-net/groupdocs.annotation.options/previewoptions/) and supply two callbacks: one that returns a writable stream for each page, and one that releases it after the page is written.

## Render pages to PNG images

Pass the two callables directly to `PreviewOptions(create_page_stream, release_page_stream)` — the library invokes `create_page_stream(page_number)` to obtain a stream for each page and `release_page_stream(page_number, page_stream)` once the page has been written. Set `preview_format` and, optionally, `page_numbers` to limit which pages are rendered.

{{< tabs "code-example-generate-document-preview" >}}
{{< tab "generate_document_preview.py" >}}
```python
import os
from groupdocs.annotation import Annotator
from groupdocs.annotation.options import PreviewOptions, PreviewFormats


def generate_document_preview():
    output_dir = "./preview"
    os.makedirs(output_dir, exist_ok=True)

    # Track the open streams so each page's file can be closed after it is written
    open_streams = {}

    def create_page_stream(page_number):
        stream = open(os.path.join(output_dir, f"page_{page_number}.png"), "wb")
        open_streams[page_number] = stream
        return stream

    def release_page_stream(page_number, page_stream):
        stream = open_streams.pop(page_number, None)
        if stream:
            stream.close()

    with Annotator("./sample.pdf") as annotator:
        preview_options = PreviewOptions(create_page_stream, release_page_stream)
        preview_options.preview_format = PreviewFormats.PNG
        preview_options.page_numbers = [1]
        annotator.document.generate_preview(preview_options)

    print(f"Generated page preview image(s) in {output_dir}.")


if __name__ == "__main__":
    generate_document_preview()
```
{{< /tab >}}
{{< /tabs >}}

`PreviewFormats` supports `PNG`, `JPEG`, and `BMP`. Other useful `PreviewOptions` properties include `width`/`height`, `resolution`, `render_comments`, and `render_annotations`.
