---
id: load-document-from-local-disk
url: annotation/java/load-document-from-local-disk
title: Load document from local disk
weight: 1
description: "The page describes how to load PDF, Word, Excel, PowerPoint documents from local disk using GroupDocs.Annotation for Java."
keywords: Load document from local disk, Load document from file path, Load document with GroupDocs.Annotation
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
{{< tab "Java" >}}
```java
// This example demonstrates loading document from file path.

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");
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
