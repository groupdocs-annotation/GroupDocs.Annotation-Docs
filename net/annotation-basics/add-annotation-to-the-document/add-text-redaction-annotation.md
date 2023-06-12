---
id: add-text-redaction-annotation
url: annotation/net/add-text-redaction-annotation
title: Add text redaction annotation
weight: 14
description: "The page describes how to add text redaction annotation to a document using GroupDocs.Annotation for .NET."
keywords: text redaction annotation, add
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
        description: Learn how to add text redaction annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of TextRedactionAnnotation class.
        - name: Specify annotation options
          text: In the TextRedactionAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name TextRedactionAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Text redaction annotation fills part of text with black rectangle to hide content like shown in the picture below:

![](/annotation/net/images/add-text-redaction-annotation.png)

You can specify the following properties of the [TextRedactionAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textredactionannotation) class:

*   [Points](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textredactionannotation/properties/points) defines annotation positions as array of points 
    

To add a text redaction annotation, follow these steps:

1.  Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.  Instantiate the [TextRedactionAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textredactionannotation) class. Specify the appropriate properties (position, page number, etc).
3.  Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [TextRedactionAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textredactionannotation) class.
4.  Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.  

The following code snippet shows how to add [TextRedactionAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textredactionannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add text redaction annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
    {
    	CreatedOn = DateTime.Now,
        Message = "This is text redaction annotation",
        BackgroundColor = 16761035,
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
     annotator.Add(textRedaction);
     annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}