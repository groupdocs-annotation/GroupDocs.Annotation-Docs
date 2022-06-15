---
id: export-annotations
url: annotation/net/export-annotations
title: Export annotations
weight: 10
description: "Following this guide you will learn how to export annotation using GroupDocs.Annotation for .NET API."
keywords: Export
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to export annotations
        description: Learn how to export annotations step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass input PDF file path as a constructor parameter.
        - name: Export annotation from XML file
          text: Call the annotator method and pass it the path to the XML file.
        - name: Save document
          text: Call Annotator class .Save() method and pass output path file.
---

Starting from version 22.1 it is possible to export annotations from an XML file.

Here is the example of the code:

```csharp
using (Annotator annotator = new Annotator("input.pdf-file")) // specify the path to the input PDF file
{
	annotator.ExportAnnotationsFromXMLFile("input.XML-file"); // specify the path to the input XML file
    annotator.Save("result_export");
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
