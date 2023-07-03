---
id: import-annotations
url: annotation/net/import-annotations
title: Import annotations
weight: 10
description: "This page describes how to import annotation from the XML files using GroupDocs.Annotation for .NET API."
keywords: Import
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to import annotations
        description: Learn how to import annotations step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass the path to the file with annotations.
        - name: Import annotation
          text: call the ImportAnnotationsFromDocument method and pass it the path to the XML file.
toc: True
---

GroupDocs.Annotation v22.1 and later allows you to import annotations from the XML files.

The following code snippet shows how to import annotations from an XML file:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf-file")) // specify the path to the file with the annotated
{
	annotator.ImportAnnotationsFromDocument("result.XML-file"); // specify the path to the result XML file
}
```
{{< /tab >}}
{{< /tabs >}}
