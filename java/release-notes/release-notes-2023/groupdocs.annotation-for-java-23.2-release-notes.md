---
id: groupdocs-annotation-for-java-23-2-release-notes
url: annotation/java/groupdocs-annotation-for-java-23-2-release-notes
title: GroupDocs.Annotation for Java 23.2 Release Notes
weight: 1
description: ""
keywords: 
productName: GroupDocs.Annotation for Java
hideChildren: False
toc: True
---

There is 1 feature and 1 bug fixed in this release.

## Full list of changes in this release

| Key | Category | Summary |
| --- | --- | --- |
| ANNOTATIONJAVA-1356 | Feature | [Add support for adjusting image quality](#support-for-adjusting-image-quality) |
| ANNOTATIONJAVA-1345 | Bug | The web application gets slow after some annotation |

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for Java 23.2:
* Set resolution (image quality) of document preview.

### Support for adjusting image quality
Now you can change image quality.
For example:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
	import com.groupdocs.annotation.Annotator;
	import com.groupdocs.annotation.options.pagepreview.PreviewOptions;

	PreviewOptions previewOptions = ...
	previewOptions.setPreviewFormat(PreviewFormats.PNG);
	try (final Annotator annotator = new Annotator(...)) {
		previewOptions.setResolution(80);
		annotator.getDocument().generatePreview(previewOptions);
	}
```
{{< /tab >}}
{{< /tabs >}}

You can change the image quality by changing the resolution value. Larger value means higher resolution. The picture shows images with a resolution of 50 and 96.

![](/annotation/java/images/resolution.png)