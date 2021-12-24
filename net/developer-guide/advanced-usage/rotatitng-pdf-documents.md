---
id: rotatitng-pdf-documents
url: annotation/net/rotatitng-pdf-documents
title: Rotating PDF documents
weight: 10
description: "Following this guide you will learn how to rotating pdf documents using GroupDocs.Annotation for .NET API."
keywords: Rotate
productName: GroupDocs.Annotation for .NET
hideChildren: False
---

Starting from version 21.12 there is an ability to rotate the page of PDF documents by 90, 180, 270 degrees, if you do not specify the page value using ProcessPages, the default will be the first.

Here is the example of the code:

```csharp
using (Annotator annotator = new Annotator("annotated_file.pdf"))
{
	annotator.ProcessPages = 1;
	annotator.Rotation = RotationDocument.on90;
    annotator.Save("result.pdf");
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
