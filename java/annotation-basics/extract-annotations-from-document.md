---
id: extract-annotations-from-document
url: annotation/java/extract-annotations-from-document
title: Extract annotations from document
weight: 4
description: "Learn how to extract annotations from document when collaborate, edit and annotate documents using GroupDocs.Annotation for Java."
keywords: Extract annotations, annotate document, get document annotations
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
    showVideo: False
    howTo:
        name: How to extract annotations from document
        description: Learn how to extract annotations from document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Obtain annotations collection from document.
        - name: Serialize class
          text: Call class XmlSerializer and pass collection of annotations to it.
        - name: Instantiate object FileStram
          text: Call an instance of a FileStream object and pass .xml file with FileMode to it.
        - name: Serialize annotation
          text: Call XmlSeerializer class .Serialize() method.
toc: True
---
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/java) allows you to extract annotations from a document and serialize them to the XML format.  

To do this, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [LoadOptions](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class and set `ImportAnnotation = true`.
3.   Define a variable of the `List<AnnotationBase>` type.
4.   Call the [get()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#get--) method to get result to variable defined on the previous step.
5.   Instantiate the `XmlSerializer` class with the `List<AnnotationBase>` type.
6.   Using `FileStreamobject`, serialize annotations to the file.

The following code snippet shows how to extract annotations from a document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to extract annotations.

LoadOptions tmp0 = new LoadOptions();

// Create an instance of Annotator class
Annotator annotator = new Annotator("InputPath", tmp0);

// Get all annotations
List<AnnotationBase> annotations = annotator.get();
```
{{< /tab >}}
{{< /tabs >}}
