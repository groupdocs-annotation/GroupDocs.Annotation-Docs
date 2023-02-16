---
id: groupdocs-annotation-for-java-latest-release-notes
url: annotation/java/release-notes/latest
title: Latest release (Febrary 2023)
weight: 1
description: ""
keywords: 
productName: GroupDocs.Annotation for Java
hideChildren: False
toc: True
---

There are 1 feature in this release.

## Full list of changes in this release

| Key | Category | Summary |
| --- | --- | --- |
| ANNOTATIONJAVA-1356 | Feature | [Add support for adjusting image quality](#support-for-adjusting-image-quality) |

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for Java 23.2:
* Set resolution (image quality) of document preview.

### Support for adjusting image quality
Now you can change image quality.
For example:

```java
PreviewOptions previewOptions = ...
previewOptions.setPreviewFormat(PreviewFormats.PNG);
try (final Annotator annotator = new Annotator(...)) {
    previewOptions.setResolution(80);
    annotator.getDocument().generatePreview(previewOptions);
}
```