---
id: load-document-from-ftp
url: annotation/java/load-document-from-ftp
title: Load document from FTP
weight: 4
description: "The page describes how to load PDF, Word, Excel, PowerPoint documents from FTP using GroupDocs.Annotation for Java."
keywords: Load document from URL, Load document by FTP GroupDocs.Annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
    showVideo: False
    howTo:
        name: How to load document from ftp
        description: Learn how to load document from ftp step by step
        steps:
        - name: Ftp web request
          text: Create a method that will create a request and pass the uniform resource identifier class to it.
        - name: Get file stream
          text: Create a method that will receive the file stream of the document and pass the web response class to it.
        - name: Load document from Ftp
          text: Create a method that will receive a file from ftp and pass the file path to it
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass method and source file path as a constructor parameter. 
        - name: Annotation class declaration
          text: Create an instance of AreaAnnotation class.
        - name: Specify annotation options 
          text: In the AreaAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name AreaAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---

The following code snippet shows how to annotate document from FTP:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates loading document from FTP.

String filePath = "sample.pdf";
String server = "localhost";

// Create an instance of Annotator class and create connection and return stream with document
Annotator annotator = new Annotator(getFileFromFtp(server, filePath));
try {
    
    // Create an instance of AreaAnnotation class and set options
    AreaAnnotation area = new AreaAnnotation();
    area.setBox(new Rectangle(100, 100, 100, 100));
    area.setBackgroundColor(65535);
    
    // Add annotation and save to file
    annotator.add(area);
    annotator.save("OutputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}

//...

private static InputStream getFileFromFtp(String server, String filePath) throws IOException {
    FTPClient client = new FTPClient();
    client.connect(server);
    InputStream inputStream = client.retrieveFileStream(filePath);
    client.disconnect();

    return inputStream;
}
```
{{< /tab >}}
{{< /tabs >}}