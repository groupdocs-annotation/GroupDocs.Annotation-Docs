---
id: load-document-from-stream
url: annotation/net/load-document-from-stream
title: Load document from stream
weight: 2
description: "The page describes how to load PDF, Word, Excel, PowerPoint documents from stream using GroupDocs.Annotation for .NET."
keywords: Load document from stream, Load document with GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to load document from stream
        description: Learn how to load document from stream step by step
        steps:
        - name: Document stream
          text: Load source file an instance documentStream with definition OpenRead
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass document stream to it. You may specify absolute or relative file path as per your requirements.
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
The following code snippet shows how to load a document from a stream:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (documentStream = File.OpenRead("input.pdf"))
using (Annotator annotator = new Annotator(documentStream))
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