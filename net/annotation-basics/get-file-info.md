---
id: get-file-info
url: annotation/net/get-file-info
title: Get file info
weight: 2
description: "This article explains how to detect document file type, size and calculate pages count when annotate documents or images with GroupDocs.Annotation."
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to get file info
        description: Learn how to get file info step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Interface IDocumentInfo
          text: Call interface IDocumentInfo and pass information about the page to it
toc: True
---
GroupDocs.Annotation allows you to get the following file information:

*   [FileType](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/idocumentinfo/properties/filetype) is a document file type (PDF, Word document, Excel spreadsheet, PowerPoint presentation or image etc.)
*   [PageCount](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/idocumentinfo/properties/pagecount) is a count of document pages
*   [FileSize](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/idocumentinfo/properties/size) is a file size;

[PagesInfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/idocumentinfo/properties/pagesinfo) represents a `List` of the [PageInfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) objects which store information about each page. 

[PageInfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) has the following properties (in pixels):
* [Width](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo/properties/width)
* [Height](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo/properties/height) in pixels. 

This properties supports all formats except Email and Html. Width and height are the same for all pages except the Cells formats.

The following code snippet shows how to get information about a document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Get file info for the file from local disk
using (Annotator annotator = new Annotator("input.docx"))
{
	IDocumentInfo info = annotator.Document.GetDocumentInfo();
    int width = info.PagesInfo[0].Width;
    int height = info.PagesInfo[0].Height;
    Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```
{{< /tab >}}
{{< /tabs >}}
