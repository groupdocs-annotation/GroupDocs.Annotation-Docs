---
id: remove-annotation-replies
url: annotation/net/remove-annotation-replies
title: Remove annotation replies
weight: 2
description: "Check this guide to learn how to remove all or specific annotation replies when collaborate over document using GroupDocs.Annotation for .NET API."
keywords: How to remove annotation reply, remove annotation reply, remove reply, reply to annotation, remove annotation comment
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
There is a quick and convenient way to remove specific or even all replies for some document annotation using **[GroupDocs.Annotation](https://products.groupdocs.com/annotation/net)** API. It is as easy as removing items from generic [List<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1) collection. In common case you have to follow these steps to delete replies:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Call [Get](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/get) method of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object and obtain collection of document annotations;
*   Access desired annotation object and remove reply in a most suitable way:
    *   call [RemoveAt(Int32)](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.removeat) or [Remove(T)](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.remove) method to remove specific reply;
    *   call [RemoveAll(Predicate<T>)](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.removeall) method to remove all replies that match the conditions defined by the specified predicate;
*   Call [Update](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/update/index) method of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object and pass annotations collection into it;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream;
    

## Remove specific annotation reply 

The easiest way for removing specific annotation reply is to delete by its index inside Replies collection. The following code sample demonstrates how to remove first annotation reply:

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

## Remove annotation replies by criteria

**[GroupDocs.Annotation](https://products.groupdocs.com/annotation/net)** API also provides a way to remove multiple annotation replies that match some criteria. The following code demonstrates how to remove replies that were added by user with name "Tom":

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

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/net/developer-guide/advanced-usage/_index.md" >}}).

### GitHub Examples
You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Annotation for .NET examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
*   [GroupDocs.Annotation for Java examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java)
*   [Document Annotation for .NET MVC UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC)
*   [Document Annotation for .NET App WebForms UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms)
*   [Document Annotation for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Dropwizard)
*   [Document Annotation for Java Spring UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Spring)
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.