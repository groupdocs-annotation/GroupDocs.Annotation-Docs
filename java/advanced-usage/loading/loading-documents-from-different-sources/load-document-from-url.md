---
id: load-document-from-url
url: annotation/java/load-document-from-url
title: Load document from URL
weight: 3
description: "The page describes how to load PDF, Word, Excel, PowerPoint documents from URL using GroupDocs.Annotation for Java."
keywords: Load document from URL, Load document by URL GroupDocs.Annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
    showVideo: False
    howTo:
        name: How to load document from Url
        description: Learn how to load document from Url step by step
        steps:
        - name: Get file stream
          text: Create a method that will receive the document stream.
        - name: Get response
          text: Create a method that will receive the response.
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass method and Url to it. You may specify absolute or relative file path as per your requirements.
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

The following example shows how to load a document using its URL:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates loading document from URL.


String url = "https://raw.githubusercontent.com/groupdocs-annotation/GroupDocs.Annotation-for-Java/master/Examples/Resources/SampleFiles/input.pdf?raw=true";

// Create an instance of Annotator class
Annotator annotator = new Annotator(new URL(url).openStream());
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