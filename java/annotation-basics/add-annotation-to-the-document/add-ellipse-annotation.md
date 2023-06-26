---
id: add-ellipse-annotation
url: annotation/java/add-ellipse-annotation
title: Add ellipse annotation
weight: 4
description: "The page describes how to add ellipse annotation to a document using GroupDocs.Annotation for Java."
keywords: ellipse, annotation, add
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
        description: Learn how to add elipse annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of EllipseAnnotation class.
        - name: Specify annotation options 
          text: In the EllipseAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name EllipseAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Ellipse annotation draws elliptic annotation on a document page like shown in the picture below.

![](/annotation/java/images/add-ellipse-annotation.png)

You can use the following methods to set the properties of the [EllipseAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation) class: 

*   [setBackgroundColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation/#setBackgroundColor-java.lang.Integer-) defines the ellipse background color
*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position on the page;
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPenColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation/#setPenColor-java.lang.Integer-) defines the pen color
*   [setPenStyle()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation/#setPenStyle-java.lang.Byte-) - defines the line style (solid, dash, dot etc.)
*   [setPenWidth()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation/#setPenWidth-java.lang.Byte-) defines the line width in pixels. 

To add an ellipse annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate [EllipseAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [EllipseAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows how to add [EllipseAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ellipseannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding ellipse annotation.

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

    // Create an instance of EllipseAnnotation class and set options
    EllipseAnnotation ellipse = new EllipseAnnotation();
    ellipse.setBackgroundColor(65535);
    ellipse.setBox(new Rectangle(100, 100, 100, 100));
    ellipse.setCreatedOn(Calendar.getInstance().getTime());
    ellipse.setMessage("This is ellipse annotation");
    ellipse.setOpacity(0.7);
    ellipse.setPageNumber(0);
    ellipse.setPenColor(65535);
    ellipse.setPenStyle(PenStyle.Dot);
    ellipse.setPenWidth((byte) 3);
    ellipse.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(ellipse);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}