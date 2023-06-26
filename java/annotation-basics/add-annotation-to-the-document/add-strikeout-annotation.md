---
id: add-strikeout-annotation
url: annotation/java/add-strikeout-annotation
title: Add strikeout annotation
weight: 12
description: "The page describes how to add strikeout annotation to a document using GroupDocs.Annotation for Java."
keywords: strikeout, add, annotation
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
        description: Learn how to add strikeout annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of StrikeoutAnnotation class.
        - name: Specify annotation options 
          text: In the StrikeoutAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name StrikeoutAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Strikeout annotation strike-throughs a text fragment like shown in the picture below:

![](/annotation/java/images/add-strikeout-annotation.png)

You can use the following methods to set the properties of the [StrikeoutAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/strikeoutannotation) class:

*   [setFontColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/strikeoutannotation/#setFontColor-java.lang.Integer-) defines the color of the annotation text
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/strikeoutannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPoints()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/strikeoutannotation/#setPoints-java.util.List-com.groupdocs.annotation.models.Point--) defines the annotation positions as array of points 
      

To add a strikeout annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [StrikeoutAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/strikeoutannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [StrikeoutAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/strikeoutannotation) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.  

  
The following code snippet shows how to add [StrikeoutAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/strikeoutannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding text strikeout annotation.

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

    // Create an instance of StrikeoutAnnotation class and set options
    StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
    strikeout.setCreatedOn(Calendar.getInstance().getTime());
    strikeout.setFontColor(65535);
    strikeout.setMessage("This is strikeout annotation");
    strikeout.setOpacity(0.7);
    strikeout.setPageNumber(0);
    strikeout.setPoints(points);
    strikeout.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(strikeout);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}