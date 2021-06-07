---
id: groupdocs-annotation-for-net-20-8-release-notes
url: annotation/net/groupdocs-annotation-for-net-20-8-release-notes
title: GroupDocs.Annotation for .NET 20.8 Release Notes
weight: 50
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 20.8{{< /alert >}}

## Major Features

Below the list of most notable changes in release of GroupDocs.Annotation for .NET 20.8:

*   Improved adding annotations to TIFF Images
*   Improved annotating images mechanism (optimized performance)
*   Added Equals operator for comparing Annotations
*   Fixed issue with open CAD files
*   Fixed failed to import annotations that was added on older versions (added backward compatibility)
*   Fixed issue with ImageData is not saving on Image annotation
*   Fixed restoring image from ImageData


Full List of Issues Covering all Changes in this Release 

| Key | Summary | Type |
| --- | --- | --- |
| ANNOTATIONNET-1418 | Improve adding annotations to TIFF Images | Improvement |
| ANNOTATIONNET-1450 | Improve ImageAnnotationHelper | Improvement |
| ANNOTATIONNET-1452 | Add comparison operator (Equals) overload for Annotation Models | Improvement |
| ANNOTATIONNET-1457 | Cad file can't be opened | Bug |
| ANNOTATIONNET-1458 | Failed to import annotations that was added on older versions | Bug |
| ANNOTATIONNET-1460 | ImageData is not saving on Image annotation | Bug |
| ANNOTATIONNET-1461 | Restore image from ImageData | Bug |

## Public API and Backward Incompatible Changes
From this time Annotation Models overload the standard Equals method and also implement the IEquatable interface with the type of the class from which this method is called.

Example how to use it:

```csharp
using (Annotator annotator = new Annotator("annotated_file.pdf"))
{
	var annotations = annotator.Get();
	ImageAnnotation imageAnnotation = new ImageAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		Opacity = 0.7,
		PageNumber = 0,
		ImagePath = "www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png",
		Angle = 100
	};
	foreach (var annotation in annotations)
	{
		if (imageAnnotation.Equals(annotation))
		{
			// Do some stuff here...
		}
	}
}
```
