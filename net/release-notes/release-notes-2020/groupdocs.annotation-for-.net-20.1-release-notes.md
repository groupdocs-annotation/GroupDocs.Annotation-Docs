---
id: groupdocs-annotation-for-net-20-1-release-notes
url: annotation/net/groupdocs-annotation-for-net-20-1-release-notes
title: GroupDocs.Annotation for .NET 20.1 Release Notes
weight: 120
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 20.1{{< /alert >}}{{< alert style="danger" >}}In this version we will remove Legacy API of GroupDocs.Annotation. So from version 20.1 GroupDocs.Annotation.Legacy. does not exist anymore{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 20.1:
*   Legacy API was removed from product
*   Added new type of annotation - Image Annotation for (SpreadSheet, Diagrams, Images, PDF, WordProcessing, Presentations)

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-880  | Implement ability to add Image annotation to PDF | Feature |
| ANNOTATIONNET-881 | Implement ability to add Image annotation to SpreadSheet | Feature |
| ANNOTATIONNET-882  | Implement ability to add Image annotation to Presentations | Feature |
| ANNOTATIONNET-883  | Implement ability to add Image annotation to WordProcessing | Feature |
| ANNOTATIONNET-1220 | Implement ability to add Image annotation to Images | Feature |
| ANNOTATIONNET-1219 | Example Code throws NullReferenceException for SpreadSheet | Bug |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 20.1. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

1.  Add Image Annotation  
    
    **Image annotation** allows to add image within document page like shown at the picture below.
    
![](annotation/net/images/groupdocs-annotation-for-net-20-1-release-notes.png)
    
{{< alert style="info" >}}IMPORTANT: On version 20.1 Image Annotation supported only in PDF, Words, Slides, Cells, Images documents.{{< /alert >}}

There is an ability to specify the next properties for ImageAnnotation type:
*   ImagePath – defines image local or remote path. Warning, if you use remote path – you need to remove http and https protocol, or www if it present. This error is now investigating.

**Not Correct:**
[https://www.google.com.ua/images/branding/googlelogo/2x/googlelogo\_color\_92x30dp.png](https://www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png)
[http://www.google.com.ua/images/branding/googlelogo/2x/googlelogo\_color\_92x30dp.png](http://www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png)

**Correct:**
[www.google.com.ua/images/branding/googlelogo/2x/googlelogo\_color\_92x30dp.png](http://www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png)
[google.com.ua/images/branding/googlelogo/2x/googlelogo\_color\_92x30dp.png](http://www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png)

*   Box - defines annotation position at document page; (image will be resized for your custom width and height)
*   Opacity - allows to set annotation opacity (present in all supported formats, examples of it you can see above);

Follow these steps to add Image annotation to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate ImageAnnotation object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass ImageAnnotation object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save) method with resultant document path or stream.
    
The following code demonstrates how to add ImageAnnotation with remote ImagePath to the document:
    
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
 	ImageAnnotation area = new ImageAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		Opacity = 0.7,
		PageNumber = 0,
		ImagePath = "www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png"
	};
	annotator.Add(area);
	annotator.Save("result.pdf");
}               
```
    
The result would be
![](annotation/net/images/groupdocs-annotation-for-net-20-1-release-notes_1.png)
