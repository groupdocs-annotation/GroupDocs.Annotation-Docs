---
id: remove-annotation-from-document
url: annotation/net/remove-annotation-from-document
title: Remove annotation from document
weight: 5
description: "Learn how to remove annotations from document when collaborate, edit and annotate documents using GroupDocs.Annotation for .NET."
keywords: Delete annotation, remove annotation, annotate document
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) provides an ability to remove all previously added annotations from document and save cleaned document as it was before annotating.  
There are the steps to remove annotations from document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [SaveOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) object and set `AnnotationTypes = AnnotationType.None`;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream and [SaveOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) object;

1) Following code demonstrates how to remove annotation from document using annotation index:

```csharp
using (Annotator annotator = new Annotator("result.xlsx"))
{
	annotator.Remove(0);
	annotator.Save("removed.xlsx");
}
```

2) Following code demonstrates how to remove annotation from document using annotation Object:

```csharp
using (Annotator annotator = new Annotator("result.xlsx"))
{
	var tmp = annotator.Get();
	annotator.Remove(tmp[0]);
	annotator.Save("removed.xlsx");
}
```

3) Following code demonstrates how to remove some annotations from document using list of Id’s:

```csharp
using (Annotator annotator = new Annotator("result.xlsx"))
{
	var idList = new List<int>{1, 2, 3};
	annotator.Remove(idList);
	annotator.Save("removed.xlsx");
}
```

4) Following code demonstrates how to remove some annotations from document using list of annotations:

```csharp
using (Annotator annotator = new Annotator("result.xlsx"))
{
	var tmp = annotator.Get();
	annotator.Remove(tmp);
	annotator.Save("removed.xlsx");
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
