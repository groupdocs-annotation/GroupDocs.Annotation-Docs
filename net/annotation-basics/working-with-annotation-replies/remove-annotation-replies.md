---
id: remove-annotation-replies
url: annotation/net/remove-annotation-replies
title: Remove annotation replies
weight: 2
description: "The page describes how to remove all or specific annotation replies when collaborate over document using GroupDocs.Annotation for .NET API."
keywords: remove annotation reply, reply to annotation, remove annotation comment
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to remove annotation replies
        description: Learn how to remove annotation replies step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Obtain annotations collection from document
        - name: Remove reply 
          text: Call AnnotationBase class .RemoveAt() method.
        - name: Update document with annotations
          text: Call Annotator class .Update() method.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
You can remove specific or all replies using the [GroupDocs.Annotation](https://products.groupdocs.com/annotation/net) API. To do this, remove the appropriate items from the [List<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1) collection. 

To delete an annotation reply (replies), follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Call the [Get](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/get) method of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class to get collection of document annotations.
3.   Access the appropriate annotation and remove a reply in a suitable way:
    *   call the [RemoveAt(Int32)](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.removeat) or [Remove(T)](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.remove) method to remove specific reply;
    *   call the [RemoveAll(Predicate<T>)](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.removeall) method to remove all replies that match the conditions defined by the  predicate.
4.   Call the [Update](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/update/index) method of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the annotations collection.
5.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.
    

## Remove specific annotation reply 

The following code snippet shows how to remove annotation reply by its index:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
// NOTE: Input document already contain annotations with replies
using (Annotator annotator = new Annotator("result.pdf"))
{
    // Obtain annotations collection from document
    List<AnnotationBase> annotations = annotator.Get();               
	// Remove first reply 
	annotations[0].Replies.RemoveAt(0);
	// Save changes
	annotator.Update(annotations);
	annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}

## Remove annotation replies by criteria

The following code snippet shows how to remove replies that match some criteria:

{{< tabs "example2">}}
{{< tab "C#" >}}
```csharp
// NOTE: Input document already contain annotations with replies
using (Annotator annotator = new Annotator("annotated_file_with_replies.pdf"))
{
    // Obtain annotations collection from document
    List<AnnotationBase> annotations = annotator.Get();
    // Remove all replies where author name is "Tom"
    annotations[0].Replies.RemoveAll(x => x.User.Name == "Tom");
    // Save changes
    annotator.Update(annotations);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}
