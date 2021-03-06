---
id: load-password-protected-documents
url: annotation/net/load-password-protected-documents
title: Load password-protected documents
weight: 1
description: "This article explains how to load password-protected PDF, Word, Excel, PowerPoint documents when using GroupDocs.Annotation for .NET."
keywords: Load password-protected document, Load protected document with GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to load document from local
        description: Learn how to load password protected documents step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass file path with password to it.
        - name: Annotation class declaration
          text: Create an instance of annotation class.
        - name: Specify annotation options 
          text: In the annotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name annotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file with class SaveOptions.
---
[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) allows to annotate documents that are protected with a password.

The following are the steps to process password-protected documents.

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with document path or stream and [LoadOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/loadoptions) object that specifies source document password;

The following code sample shows how to work with password-protected documents.

```csharp
using (Annotator annotator = new Annotator("input.pdf", new LoadOptions() { Password = "1234" }))
{
 	AreaAnnotation area = new AreaAnnotation()
    {
       	Box = new Rectangle(100, 100, 100, 100),
       	BackgroundColor = 65535,
    };
    annotator.Add(area);
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