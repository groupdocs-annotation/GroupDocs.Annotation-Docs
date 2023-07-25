---
id: load-document-from-local-disk
url: annotation/net/load-document-from-local-disk
title: Load document from local disk
weight: 1
description: "The page describes how to load PDF, Word, Excel, PowerPoint documents from local disk using GroupDocs.Annotation for .NET."
keywords: Load document from local disk, Load document from file path, Load document with GroupDocs.Annotation
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
        description: Learn how to load document from local step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
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

The following code snippet shows how to load documents from local disk:

{{< tabs "example1">}}
{{< tab "C#" >}}
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
{{< /tab >}}
{{< /tabs >}}
