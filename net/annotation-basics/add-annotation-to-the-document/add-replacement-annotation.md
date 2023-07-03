---
id: add-replacement-annotation
url: annotation/net/add-replacement-annotation
title: Add replacement annotation
weight: 10
description: "The page describes how to add replacement annotation to a document using GroupDocs.Annotation for .NET."
keywords: replacement annotation, add
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
        description: Learn how to add replaacment annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of ReplacementAnnotation class.
        - name: Specify annotation options 
          text: In the ReplacementAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ReplacementAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Replacement annotation replaces original text with specified text fragmentas shown in the picture below: 

![](/annotation/net/images/add-replacement-annotation.png)

You can specify the following properties of the [ReplacementAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/replacementannotation) class:

*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation/properties/fontcolor) defines the color of annotation text
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation/properties/opacity) allows you to set the annotation opacity
*   [Points](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation/properties/points) defines the annotation positions as array of points
*   [TextToReplace](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation/properties/texttoreplace) defines the replacement text   
     

To add a replacement annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [ReplacementAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/replacementannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [ReplacementAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/replacementannotation) class.
4.  Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream. 

  

The following code snippet shows how to add [ReplacementAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/replacementannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add replacement annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	ReplacementAnnotation replacement = new ReplacementAnnotation
    {
    	CreatedOn = DateTime.Now,
        FontColor = 65535,
        Message = "This is replacement annotation",
        Opacity = 0.7,
        PageNumber = 0,
        FontSize = 11,
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
         },
         TextToReplace = "replaced text"
     };
     annotator.Add(replacement);
     annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}