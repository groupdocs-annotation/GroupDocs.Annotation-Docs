---
id: groupdocs-annotation-for-net-20-7-release-notes
url: annotation/net/groupdocs-annotation-for-net-20-7-release-notes
title: GroupDocs.Annotation for .NET 20.7 Release Notes
weight: 60
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 20.7{{< /alert >}}

## Major Features

Below the list of most notable changes in  release of GroupDocs.Annotation for .NET 20.7:

*   Implemented Angle property for Image Annotation
*   Implemented horizontal and vertical alignment for Watermark
*   Implemented text horizontal alignment for TextField
*   Fixed saving only specific annotation types for html, email, words and image
*   Improved exceptions usage
*   Fixed incorrect position of text annotations types in Cells


Full List of Issues Covering all Changes in this Release 

| Key | Summary | Type |
| --- | --- | --- |
| ANNOTATIONNET-1421 | Implement horizontal text alignment TextField and TextWatermark annotations | Feature |
| ANNOTATIONNET-1427 | Improve CellsInfo method in DocumentInfoExtractor | Improvement |
| ANNOTATIONNET-1355 | Improve exceptions usage. | Improvement |
| ANNOTATIONNET-1426 | Incorrect vertical position of the text annotations on Excel files. | Bug |
| ANNOTATIONNET-1425 | Exception 'Failed extract annotations from images' during removing annotations from PNG. | Bug |
| ANNOTATIONNET-1424 | Stream is used by another process after Images CleanUp |	Bug |
| ANNOTATIONNET-1415 | Corrupted or damaged file error | Bug |
| ANNOTATIONNET-1420 | Saving Html with Images throws exception | Bug |


## Public API and Backward Incompatible Changes
New two enumeration types have been added in version 20.7. *HorizontalAlignment* represents annotations horizontal alignment state and *VerticalAlignment* represents annotations vertical alignment state.

## 1\. Added Angle property for ImageAnnotation
To set a custom angle for ImageAnnotation, you can use the new *Angle* property. Angle is measured in degrees.

Example how to use it:

```csharp
ImageAnnotation imageAnnotation = new ImageAnnotation
{
	Box = new Rectangle(100, 100, 100, 100),
	Opacity = 0.7,
	PageNumber = 0,
	ImagePath = "image.png",
	Angle = 90
};
```

## 2\. Added horizontal and vertical alignment for Watermark
To set Horizontal and Vertical Alignments for WatermarkAnnotation, you can use Alignment properties.

```csharp
WatermarkAnnotation watermarkAnnotation = new WatermarkAnnotation()
{
	VerticalAlignment = VerticalAlignment.Bottom,
	HorizontalAlignment = HorizontalAlignment.Left
};
```


## 3\. Added text horizontal alignment for TextField
To set a text horizontal alignment you can use the TextHorizontalAlignment property.

```csharp
TextFieldAnnotation textFieldAnnotation = new TextFieldAnnotation()
{
	TextHorizontalAlignment = HorizontalAlignment.Left
};
```

