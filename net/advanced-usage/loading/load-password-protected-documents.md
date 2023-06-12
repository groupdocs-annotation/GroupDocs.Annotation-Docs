---
id: load-password-protected-documents
url: annotation/net/load-password-protected-documents
title: Load the password-protected documents
weight: 1
description: "The article describes how to load the password protected PDF, Word, Excel, PowerPoint documents using GroupDocs.Annotation for .NET."
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
toc: True
---

[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) allows to annotate documents that are protected with a password.

To load a password protected file, follow these steps:

1. Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the document path or stream.
2. Instantiate the [LoadOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/loadoptions) class. Specify the source document password as a parameter.

The following code snippet shows how to load a password protected file:

{{< tabs "example1">}}
{{< tab "C#" >}}
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
{{< /tab >}}
{{< /tabs >}}