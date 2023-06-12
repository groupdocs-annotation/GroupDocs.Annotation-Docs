---
id: add-ellipse-annotation
url: annotation/net/add-ellipse-annotation
title: Add ellipse annotation
weight: 4
description: "The page describes how to add ellipse annotation to a document using GroupDocs.Annotation for .NET."
keywords: ellipse, annotation, add
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
        description: Learn how to add elipse annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of EllipseAnnotation class.
        - name: Specify annotation options 
          text: In the EllipseAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name EllipseAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Ellipse annotation draws elliptic annotation on a document page like shown in the picture below.

![](/annotation/net/images/add-ellipse-annotation.png)

You can set the following properties of the [EllipseAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/ellipseannotation) class: 

*   [BackgroundColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/backgroundcolor) defines the ellipse background color
*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/box) defines the annotation position on the page;
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) allows you to set the annotation opacity
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/pencolor) defines the pen color
*   [PenStyle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/penstyle) - defines the line style (solid, dash, dot etc.)
*   [PenWidth](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/penwidth) defines the line width in pixels. 

To add an ellipse annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate [EllipseAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/ellipseannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [EllipseAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/ellipseannotation) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [EllipseAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/ellipseannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add ellipse annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	EllipseAnnotation ellipse = new EllipseAnnotation
    {
    	BackgroundColor = 65535,
        Box = new Rectangle(100, 100, 100, 100),
        CreatedOn = DateTime.Now,
        Message = "This is ellipse annotation",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = 65535,
        PenStyle = PenStyle.Dot,
        PenWidth = 3,
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
   annotator.Add(ellipse);
   annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}