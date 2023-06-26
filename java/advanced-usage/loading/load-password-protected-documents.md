---
id: load-password-protected-documents
url: annotation/java/load-password-protected-documents
title: Load the password-protected documents
weight: 1
description: "The article describes how to load the password protected PDF, Word, Excel, PowerPoint documents using GroupDocs.Annotation for Java."
keywords: Load password-protected document, Load protected document with GroupDocs.Annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
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

[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/java) allows to annotate documents that are protected with a password.

To load a password protected file, follow these steps:

1. Instantiate the [LoadOptions](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the source document password as a parameter.
2. Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the document path or stream and the the [LoadOptions](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object.


The following code snippet shows how to load a password protected file:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates annotating documents that are protected with a password.

// Create an instance of LoadOptions class and set password
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("1234");

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath", loadOptions);
try {
    // Create an instance of AreaAnnotation class and set options
    AreaAnnotation area = new AreaAnnotation();
    area.setBox(new Rectangle(100, 100, 100, 100));
    area.setBackgroundColor(65535);
    
    // Add annotation and save to file
    annotator.add(area);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}