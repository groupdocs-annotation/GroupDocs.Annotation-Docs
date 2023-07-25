---
id: export-annotations
url: annotation/net/export-annotations
title: Export annotations
weight: 10
description: "The page describes how to export annotation using GroupDocs.Annotation for .NET API."
keywords: import
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
toc: True
---

GroupDocs v22.1 allows you to export annotations from a document to an XML file.

The following code snippet shows how to export annotations:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf-file")) // specify the path to the input PDF file
{
	annotator.ExportAnnotationsFromXMLFile("input.XML-file"); // specify the path to the input XML file
    annotator.Save("result_export");
}
```
{{< /tab >}}
{{< /tabs >}}
