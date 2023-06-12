---
id: put-image-annotation-over-text
url: annotation/net/put-image-annotation-over-text
title: Put image annotations over the text using ZIndex
weight: 8
description: "This page describes how to set image ZIndex to place it over the text"
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to put image annotation over text
        description: Learn how to put image annotation over text step by step
        steps:
        - name: Annotation class declaration
          text: Create an instance of ImageAnnotation class.
        - name: Specify annotation options 
          text: In the ImageAnnotation class constructor, pass parameters.
toc: True
---

GroupDocs.Annotation v21.5 and later allows you to specify images placing order for the Word file formats. To do this, set the [ZIndex](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/zindex) property of the [ImageAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation) class.

The following code snippets shows how to specify aZIndex of the image annotation:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
ImageAnnotation area = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png",
    Angle = 100,
    ZIndex = 3
};
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}The feature is supported for Words files only. Other formats ignore this property{{< /alert >}}

