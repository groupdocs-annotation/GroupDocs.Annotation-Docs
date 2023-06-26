---
id: save-specific-page-range
url: annotation/java/save-specific-page-range
title: Save specific page range
weight: 3
description: "This article demonstrates how to save specific page range when annotating documents using GroupDocs.Annotation for Java API."
keywords: Save specific annotated pages, save specific pages
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
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

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [SaveOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/) class. Call the [setFirstPage](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/#setFirstPage-int-) and  [setLastPage](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/#setLastPage-int-) methods to specify parameters.
3.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method with the resultant document path or stream. Specify the [SaveOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/) class as a parameter.

The following code demonstrates how to save the range of document page:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates saving result document with specified pages.

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");
try {
    SaveOptions tmp0 = new SaveOptions();
    tmp0.setFirstPage(2);
    tmp0.setLastPage(4);
    
    // Save to file
    annotator.save(outputPath, tmp0);
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}