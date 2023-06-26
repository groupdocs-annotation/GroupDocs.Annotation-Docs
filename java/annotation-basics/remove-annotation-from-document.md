---
id: remove-annotation-from-document
url: annotation/java/remove-annotation-from-document
title: Remove annotation from document
weight: 5
description: "Learn how to remove annotations from document when collaborate, edit and annotate documents using GroupDocs.Annotation for Java."
keywords: Delete annotation, remove annotation, annotate document
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
        - name: Method Remove
          text: Call Annotator class method .Remove()
        - name: Save document
          text: Call Annotator class method .Save() and pass output path file to it.
toc: True
---
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/javaa) allows you to remove all previously added annotations. To do this, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [SaveOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/) class. Set `AnnotationTypes = AnnotationType.None`.
3.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows how to remove annotation using its index:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to remove annotations from document.

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.None);

// Save result to file
annotator.save("outputPath", saveOptions);
```
{{< /tab >}}
{{< /tabs >}}