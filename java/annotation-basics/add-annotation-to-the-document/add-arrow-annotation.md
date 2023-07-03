---
id: add-arrow-annotation
url: annotation/java/add-arrow-annotation
title: Add arrow annotation
weight: 2
description: "The page describes how to add arrow annotation to a document using GroupDocs.Annotation for Java."
keywords: arrow annotation, add
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
        description: Learn how to add arrow annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of ArrowAnnotation class.
        - name: Specify annotation options 
          text: In the ArrowAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ArrowAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Arrow annotation draws an arrow on the document page and annotate it as shown in the picture below. 

![](/annotation/java/images/add-arrow-annotation.png)

You can use the following methods to set the properties of the [ArrowAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/) class:

*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines annotation position at document page
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPenColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/#setPenColor-java.lang.Integer-) defines the arrow color
*   [setPenStyle()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/#setPenStyle-java.lang.Byte-) defines annotation line style (solid, dash, dot etc.)
*   [setPenWidth()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/#setPenWidth-java.lang.Byte-) defines the arrow line width in pixels

To add an arrow annotation to document, follow these steps:  

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [ArrowAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/) class. Set the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [ArrowAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.  

The following code snippet shows how to add [ArrowAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/arrowannotation/) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding arrow annotation.

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");
try {
    // Create an instance of Reply class and add comments
    Reply reply1 = new Reply();
    reply1.setComment("First comment");
    reply1.setRepliedOn(Calendar.getInstance().getTime());

    Reply reply2 = new Reply();
    reply2.setComment("Second comment");
    reply2.setRepliedOn(Calendar.getInstance().getTime());

    java.util.List<Reply> replies =  new ArrayList<Reply>();
    replies.add(reply1);
    replies.add(reply2);

    // Create an instance of ArrowAnnotation class and set options
    ArrowAnnotation arrow = new ArrowAnnotation();
    arrow.setBox(new Rectangle(100, 100, 100, 100));
    arrow.setCreatedOn(Calendar.getInstance().getTime());
    arrow.setMessage("This is arrow annotation");
    arrow.setOpacity(0.7);
    arrow.setPageNumber(0);
    arrow.setPenColor(65535);
    arrow.setPenStyle(PenStyle.Dot);
    arrow.setPenWidth((byte) 3);
    arrow.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(arrow);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}
