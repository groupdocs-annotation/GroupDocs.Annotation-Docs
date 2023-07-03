---
id: add-link-annotation
url: annotation/net/add-link-annotation
title: Add link annotation
weight: 7
description: "The page describes how to add link annotation to a document using GroupDocs.Annotation for .NET."
keywords: link annotation,add
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
        description: Learn how to add link annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of LinkAnnotation class.
        - name: Specify annotation options 
          text: In the LinkAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name LinkAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Link annotation adds a hyperlink to document as shown in the picture below:

![](/annotation/net/images/add-link-annotation.png)

You can set the following properties of the  [LinkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/linkannotation) class:

*   [Url](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation/properties/url) defines link to a web resource
*   [Points](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation/properties/points) defines the annotation positions as an array of points.  
    

To add a link annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [LinkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/linkannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [LinkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/linkannotation) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [LinkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/linkannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add link annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	LinkAnnotation link= new LinkAnnotation
    {
    	Url = "https://www.groupdocs.com/",
        CreatedOn = DateTime.Now,
        Message = "This is link annotation",
        BackgroundColor = 65535,
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
    annotator.Add(link);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}