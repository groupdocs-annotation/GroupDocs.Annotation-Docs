---
id: add-resource-redaction-annotation
url: annotation/net/add-resource-redaction-annotation
title: Add resource redaction annotation
weight: 11
description: "The page describes how to add resource redaction annotation to a document using GroupDocs.Annotation for .NET."
keywords: resource redaction, add
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
        description: Learn how to add resource redaction annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements
        - name: Annotation class declaration. 
          text: Create an instance of ResourcesRedactionAnnotation class.
        - name: Specify annotation options 
          text: In the ResourcesRedactionAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ResourcesRedactionAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Resource redaction annotation fills black rectangle with fixed position to hide a text like shown in the picture below:

![](/annotation/net/images/add-resource-redaction-annotation.png)

You can specify the following properties of the [ResourcesRedactionAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) class:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation/properties/box) defines the annotation on the page

To add a resource redaction annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
*   Instantiate the [ResourceRedactionAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) class. Specify the appropriate properties (position, page number, etc).
*   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [ResourceRedactionAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) class.
4.  Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream. 

The following code snippet shows how to add [ResourcesRedactionAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add resource redaction annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	ResourcesRedactionAnnotation resourcesRedaction = new ResourcesRedactionAnnotation
    {
    	Box = new Rectangle(100, 100, 100, 100),
        CreatedOn = DateTime.Now,
        Message = "This is resources redaction annotation",
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
   annotator.Add(resourcesRedaction);
   annotator.Save("result.pdf");
} 

```
{{< /tab >}}
{{< /tabs >}}