---
id: update-annotation-replies
url: annotation/net/update-annotation-replies
title: Update annotation replies
weight: 3
description: "The page describes how to update annotation replies when collaborate over document using GroupDocs.Annotation for .NET API."
keywords: update annotation reply, change reply, reply to annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to update replies to annotation
        description: Learn how to update replies annotation step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Obtain annotations collection from document
        - name: Update reply 
          text: set the Comment parameter of the AnnotationBase class
        - name: Update document with annotations
          text: Call Annotator class .Update() method.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/net) provides an ability to update annotation replies by accessing them using the [Replies](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/annotationbase/properties/replies) collection.

To update annotation replies, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Call the [Get](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/get) method of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class to get collection of the document annotations.
3.   Access a reply object in the [Replies](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/annotationbase/properties/replies) collection using its index (zero-based) and update its properties.
4.   Call the [Update](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/update) method of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify annotations.
5.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream and the [SaveOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) class.
    

The following code snippet shows how to update reply by index: 

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
// NOTE: Input document already contain annotations with replies
using (Annotator annotator = new Annotator("result.pdf"))
{
	// Obtain annotations collection from document
	List<AnnotationBase> annotations = annotator.Get();
                
	// Update first annotation first reply
	annotations[0].Replies[0].Comment = "Updated reply";
                
	// Save changes
	annotator.Update(annotations);
	annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}