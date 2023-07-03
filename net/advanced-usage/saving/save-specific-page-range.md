---
id: save-specific-page-range
url: annotation/net/save-specific-page-range
title: Save specific page range
weight: 3
description: "This article demonstrates how to save specific page range when annotating documents using GroupDocs.Annotation for .NET API."
keywords: Save specific annotated pages, save specific pages
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to annotate a document
        description: Learn how to add area annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Save document
          text: Call Annotator class .Save() method and pass output path file and in the SaveOptions class set FirstPage and LastPage .
toc: True
---

To export the specific page range, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [SaveOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) class. Specify the [FirstPage](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions/firstpage/) and  [LastPage](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions/lastpage/) parameters.
3.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with the output document path or stream. Specify the [SaveOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) class as a parameter.

The following code demonstrates how to save the range of document page:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
// for this example input document ("input.pdf") must have at least 4 pages
using (Annotator annotator = new Annotator("input.pdf"))
{
	//Result file will be contain only 3 pages (2, 3 and 4 page)
	annotator.Save("result.pdf", new SaveOptions { FirstPage = 2, LastPage = 4 });
}
```
{{< /tab >}}
{{< /tabs >}}