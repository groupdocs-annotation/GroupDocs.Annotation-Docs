---
id: load-document-from-local-disk
url: annotation/net/load-document-from-local-disk
title: Load document from local disk
weight: 1
description: "This article explains how to load PDF, Word, Excel, PowerPoint documents from local disk when using GroupDocs.Annotation for .NET."
keywords: Load document from local disk, Load document from file path, Load document with GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
When the source document is located on the local disk [**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) allows you to load it via [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class constructor specifying absolute or relative path to it.   
Following code snippet shows how to load documents from local disk.

```csharp
using (Annotator annotator = new Annotator("source.docx"))
{
	AreaAnnotation area = new AreaAnnotation()
       {
       	Box = new Rectangle(100, 100, 100, 100),
       	BackgroundColor = 65535,
       };
       annotator.Add(area);
       annotator.Save("result.pdf", new SaveOptions());
}

```

## More resources

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
