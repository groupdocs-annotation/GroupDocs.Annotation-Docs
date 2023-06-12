---
id: add-distance-annotation
url: annotation/net/add-distance-annotation
title: Add distance annotation
weight: 3
description: "The page describes how to add distance annotation to a document using GroupDocs.Annotation for .NET."
keywords: distance annotation, add annotation
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
        description: Learn how to add distance annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of DistanceAnnotation class.
        - name: Specify annotation options 
          text: In the DistanceAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name DistanceAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Distance annotation shows a distance between objects in a document like shown in the picture below: 

![](/annotation/net/images/add-distance-annotation.png)

You can set the following properties of the [DistanceAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/distanceannotation) class:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/box) defines annotation position on a page
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) allows you to set the annotation opacity
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/pencolor) defines the annotation color
*   [PenStyle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/penstyle) defines the annotation line style (solid, dash, dot etc.)
*   [PenWidth](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/penwidth) defines the line width in pixels

  
To add a distance annotation to document, follow these steps:  

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [DistanceAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/distanceannotation) class. Set the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [DistanceAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/distanceannotation) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.  
      
    

The following code snippet shows how to add [DistanceAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/distanceannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add distance annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	DistanceAnnotation distance = new DistanceAnnotation
    {
        Box = new Rectangle(200, 150, 200, 30),
        CreatedOn = DateTime.Now,
        Message = "This is distance annotation",
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
    annotator.Add(distance);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}
