---
id: add-point-annotation
url: annotation/net/add-point-annotation
title: Add point annotation
weight: 8
description: "The page describes how to add point annotation to a document using GroupDocs.Annotation for .NET."
keywords: point annotation, add
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
        description: Learn how to add point annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of PointAnnotation class.
        - name: Specify annotation options 
          text: In the PointAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name PointAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Point annotation sticks comments to any point in a document like shown in the picture below:

![](/annotation/net/images/add-point-annotation.png)

You can specify the following properties of the [PointAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/pointannotation) class:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/pointannotation/properties/box) defines the annotation position on the page
    

To add a point annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
*   Instantiate the [PointAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/pointannotation) class. Specify the appropriate properties (position, page number, etc).
*   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [PointAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/pointannotation) class.
4.  Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream. 

The following code snippet shows how to add [PointAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/pointannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add point annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	PointAnnotation point = new PointAnnotation
    {
    	Box = new Rectangle(100, 100, 0, 0),
        CreatedOn = DateTime.Now,
        Message = "This is point annotation",
        PageNumber = 0,
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
    annotator.Add(point);
    annotator.Save("result.pdf"));
} 
```
{{< /tab >}}
{{< /tabs >}}