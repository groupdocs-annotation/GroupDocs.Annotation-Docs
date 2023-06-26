---
id: add-underline-annotation
url: annotation/java/add-underline-annotation
title: Add underline annotation
weight: 15
description: "The page describes how to add an underline annotation to a document using GroupDocs.Annotation for Java."
keywords: underline, add, annotation
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
        description: Learn how to add underline annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Annotation class declaration 
          text: Create an instance of UnderlineAnnotation class.
        - name: Specify annotation options
          text: In the UnderlineAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name UnderlineAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Underline annotation underlines text like shown in the picture below:

![](/annotation/java/images/add-underline-annotation.png)

You can use the following methods to set the properties of the [UnderlineAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/underlineannotation) class:

*   [setFontColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/underlineannotation/#setFontColor-java.lang.Integer-) defines the color of the annotation text
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/underlineannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPoints()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/underlineannotation/#setPoints-java.util.List-com.groupdocs.annotation.models.Point--) defines the annotation positions as array of points
*   [setUnderlineColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/underlineannotation/#setUnderlineColor-java.lang.Integer-) defines the color of the underline line

To add an underline annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [UnderlineAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/underlineannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [UnderlineAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/underlineannotation) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows how to add [UnderlineAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/underlineannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding text underline annotation.

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

    Point point1 = new Point(80, 730);
    Point point2 = new Point(240, 730);
    Point point3 = new Point(80, 650);
    Point point4 = new Point(240, 650);

    List<Point> points = new ArrayList<Point>();
    points.add(point1);
    points.add(point2);
    points.add(point3);
    points.add(point4);

    // Create an instance of AreaAnnotation class and set options
    UnderlineAnnotation underline = new UnderlineAnnotation();
    underline.setCreatedOn(Calendar.getInstance().getTime());
    underline.setFontColor(65535);
    underline.setMessage("This is underline annotation");
    underline.setOpacity(0.1);
    underline.setPageNumber(0);
    underline.setPoints(points);
    underline.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(underline);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}