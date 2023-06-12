---
id: add-squiggly-annotation
url: annotation/net/add-squiggly-annotation
title: Add squiggly annotation
weight: 15
description: "The page describes how to add squiggly annotation to a document using GroupDocs.Annotation for .NET."
keywords: squiggly annotation, add annotation
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
        description: Learn how to add squiggly annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of SquigglyAnnotation class.
        - name: Specify annotation options 
          text: In the SquigglyAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name SquigglyAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Squiggly annotation marks text with a squiggly styling like shown in the picture below:

![](/annotation/net/images/add-squiggly-annotation.png)

You can specify the following properties of the [SquigglyAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/squigglyannotation) class:

*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation/properties/fontcolor) defines the color of the annotation text
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation/properties/opacity) allows you to set the annotation opacity
*   [Points](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation/properties/points) defines the annotation positions as array of points 
*   [BackgroundColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/backgroundcolor) defines the area background color
*   [SquigglyColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation/properties/squigglycolor) defines the annotation line color

To add a squiggly annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [SquigglyAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/squigglyannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [SquigglyAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/squigglyannotation) class;
4.  Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.  

The following code snippet shows how to add [SquigglyAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/squigglyannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add squiggly annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	SquigglyAnnotation squiggly = new SquigglyAnnotation
    {
    	CreatedOn = DateTime.Now,
        FontColor = 65535,
        BackgroundColor = 16761035,
        Message = "This is squiggly annotation",
        Opacity = 0.7,
        PageNumber = 0,
        SquigglyColor = 1422623, //Supported only Word and PDF
        Points = new List<Point>
        {
        	new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
        },
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
    annotator.Add(squiggly);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}