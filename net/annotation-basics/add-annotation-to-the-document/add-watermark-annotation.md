---
id: add-watermark-annotation
url: annotation/net/add-watermark-annotation
title: Add watermark annotation
weight: 16
description: "The page describes how to add watermark annotation to a document using GroupDocs.Annotation for .NET."
keywords: watermark, annotation, add
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to annotate a document
        description: Learn how to add watermark annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of WatermarkAnnotation class.
        - name: Specify annotation options
          text: In the WatermarkAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name WatermarkAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Watermark annotation adds text watermark as shown in the picture below:

![](/annotation/net/images/add-watermark-annotation.png)

You can specify the following properties of the [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) class:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/box) defines the annotation position at the document page
*   [Text](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/text) defines the watermark text
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontcolor) defines the color of the annotation text
*   [FontFamily](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontfamily) defines the font of the annotation text
*   [FontSize](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontsize) defines the text font size. If the `AutoScale` property is `true`, GroupDocs.Annotation ignores this property
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/opacity) allows you to set the annotation opacity
*   [Angle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/angle) defines the watermark text angle
*   [VerticalAlignment](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/verticalalignment/)  defines the vertical alignment
*   [HorizontalAlignment](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/horizontalalignment/) defines the horizontal alignment
*   [AutoScale](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/autoscale/) sets the watermark size  depending on the word length and the page size. If this property is `true`, GroupDocs.Annotation ignores the `FontSize` property

To add a watermark annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

  

The following code snippet shows demonstrates how to add [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add watermark annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	WatermarkAnnotation watermark = new WatermarkAnnotation
    {
    	Angle = 75,
        Box = new Rectangle(200, 200, 100, 50),
        CreatedOn = DateTime.Now,
        Text = "Watermark",
        FontColor = 65535,
        FontSize = 12,
        Message = "This is watermark annotation",
        Opacity = 0.7,
        AutoScale = true,
        HorizontalAlignment = HorizontalAlignment.Center,
        VerticalAlignment = VerticalAlignment.Center,
        Replies = new List<Reply>
        {
        	new Reply
            {
            	Comment = "First comment",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
            	Comment = "Second comment",
                RepliedOn = DateTime.Now
            }
        }
    };
    annotator.Add(watermark);
    annotator.Save("result.pdf");
} 
```
{{< /tab >}}
{{< /tabs >}}.