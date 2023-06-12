---
id: how-to-add-watermark-to-documents
url: annotation/net/how-to-add-watermark-to-documents
title: How to add watermarks to photo or documents in .NET
weight: 6
description: "Programmatically add watermarks to any document, including photos, PDF, word, excell sheets and others using .NET API."
keywords: watermark, watermark photos, add watermark, save watermark, documents watermark
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to add watermark to the document using .NET API.
    showVideo: False
    howTo:
        name: How to add watermark annotation
        description: Learn how to programmatically add watermark annotation to the any document
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Create watermark object
            text: Create an instance of WatermarkAnnotation class.
          - name: Specify watermark options 
            text: Pass parameters to the WatermarkAnnotation constructor.
          - name: Add watermark annotation to the document
            text: Call method Add() on Annotator object and pass WatermarkAnnotation instance there.
          - name: Save document with annotation
            text: Call method Save() on Annotator object and pass output file destination there.
toc: True
---

## Overview

GroupDocs.Annotation considers the watermark as one of the annotations. You can add a text watermark to a document of any supported [format] (https://docs.groupdocs.com/annotation/net/supported-document-formats/). You can specify the text, and choose the font, color, size, transparency, angle, and other options for the text. For details, see [Add watermark annotation](https://docs.groupdocs.com/annotation/net/add-watermark-annotation/).

Currently, GroupDocs.Annotation only allows you to create text annotations. To add other watermarks, use the [GroupDocs.Watermark] (https://products.groupdocs.com/watermark/net/) product.

## How to add watermark to a document

**Watermark** annotation adds text watermark like shown at the picture below:

![](/annotation/net/images/add-watermark-annotation.png)

You can specify the following properties of [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation):

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/box) defines annotation position at document page;
*   [Text](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/text) specifies text of watermark;
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontcolor) sets color of annotation text;
*   [FontFamily](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontfamily) sets font of annotation text;
*   [FontSize](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontsize) sets size of text font;
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/opacity) defines annotation opacity;
*   [Angle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/angle) defines the watermark text angle;
*   [VerticalAlignment](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/verticalalignment/) defines vertical alignment on document;
*   [HorizontalAlignment](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/horizontalalignment/) defines horizontal alignment on document.
*   [AutoScale](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/autoscale/) sets the watermark size depends on the word length and document size.

To add Watermark annotation to document, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream;
2.   Instantiate the [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) object. Specify the appropriate properties (position, color, etc);
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) object;
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) to the document:

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
{{< /tabs >}}