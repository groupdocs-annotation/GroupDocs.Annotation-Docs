---
id: add-highlight-annotation
url: annotation/net/add-highlight-annotation
title: Add highlight annotation
weight: 5
description: "The page describes how to add highlight annotation to a document using GroupDocs.Annotation for .NET."
keywords: highlight, annotation, add
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
        description: Learn how to add highlight annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of HighlightAnnotation class.
        - name: Specify annotation options 
          text: In the HighlightAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name HighlightAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Highlight annotation highlights and comments selected text as shown in the picture below:

![](/annotation/net/images/add-highlight-annotation.png)

You can set the following properties of the [HighlightAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) class:

*   [BackgroundColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/backgroundcolor) defines the annotation background color
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation/properties/fontcolor) defines the color of annotation text
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) - allows you to set the annotation opacity
*   [Points](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation/properties/points) defines the annotation positions as an array of points

To add a highlight annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate [HighlightAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [HighlightAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream. 
      
    

The following code snippet shows how to add [HighlightAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add highlight annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	HighlightAnnotation highlight = new HighlightAnnotation
    {
    	BackgroundColor = 65535,
        CreatedOn = DateTime.Now,
        FontColor = 0,
        Message = "This is highlight annotation",
        Opacity = 0.5,
        PageNumber = 0,
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
    annotator.Add(highlight);
    annotator.Save("result.pdf");
} 

```
{{< /tab >}}
{{< /tabs >}}