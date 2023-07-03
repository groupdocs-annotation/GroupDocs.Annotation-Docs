---
id: get-file-info
url: annotation/java/get-file-info
title: Get file info
weight: 2
description: "This page describes how to detect document file type, size and calculate pages count when annotate documents or images with GroupDocs.Annotation."
keywords: 
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
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

*   [FileType](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/idocumentinfo/#getFileType--) is a document file type (PDF, Word document, Excel spreadsheet, PowerPoint presentation or image etc.)
*   [PageCount](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/idocumentinfo/#getPageCount--) is a count of document pages
*   [FileSize](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/idocumentinfo/#getSize--) is a file size;

[PagesInfo](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/idocumentinfo/#setPagesInfo-java.util.List-com.groupdocs.annotation.models.PageInfo--) represents a `List` of the [PageInfo](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/pageinfo/) objects which store information about each page. 

[PageInfo](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/pageinfo/) has the following properties (in pixels):
* [Width](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/pageinfo/#getWidth--)
* [Height](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/pageinfo/#getHeight--) in pixels. 

This properties supports all formats except Email and Html. Width and height are the same for all pages except the Cells formats.

The following code snippet shows how to get information about a document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates document info extraction

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");
try {
	
	// Get document info
	IDocumentInfo info = annotator.getDocument().getDocumentInfo();
	System.out.println(
		"\nFile type: "+info.getFileType()
		+"\nNumber of pages: "+info.getPageCount()
		+"\nDocument size: {2} bytes"+info.getSize()
	);    
} finally {
	if (annotator != null) {
		annotator.dispose();
	}
}
```
{{< /tab >}}
{{< /tabs >}}
