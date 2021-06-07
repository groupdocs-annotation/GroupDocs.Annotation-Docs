---
id: update-annotation-replies
url: annotation/net/update-annotation-replies
title: Update annotation replies
weight: 3
description: "Check this guide to learn how to update annotation replies when collaborate over document using GroupDocs.Annotation for .NET API."
keywords: How to change or remove annotation reply, update annotation reply, remove reply, reply to annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) provides and ability to programmatically update annotation replies by accessing them by their index inside [Replies](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/annotationbase/properties/replies) collection.

Here is a steps to update annotation reply (considered that we already have some reply added to annotation)
*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Call [Get](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/get) method of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object and obtain collection of document annotations;
*   Access desired reply object inside [Replies](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/annotationbase/properties/replies) collection by its index (zero-based) and update its properties as needed;
*   Call [Update](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/update) method of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with passed annotations;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream and [SaveOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) object;
    

The following code demonstrates how to update reply by index: 

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
