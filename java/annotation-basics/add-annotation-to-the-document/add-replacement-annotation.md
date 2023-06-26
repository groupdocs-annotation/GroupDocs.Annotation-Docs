---
id: add-replacement-annotation
url: annotation/java/add-replacement-annotation
title: Add replacement annotation
weight: 10
description: "The page describes how to add replacement annotation to a document using GroupDocs.Annotation for Java."
keywords: replacement annotation, add
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
        description: Learn how to add replaacment annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of ReplacementAnnotation class.
        - name: Specify annotation options 
          text: In the ReplacementAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ReplacementAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Replacement annotation replaces original text with specified text fragmentlike shown in the picture below: 

![](/annotation/java/images/add-replacement-annotation.png)

You can use the following methods to set the properties of the [ReplacementAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/replacementannotation) class:

*   [setFontColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/replacementannotation/#setFontColor-java.lang.Integer-) defines the color of annotation text
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/replacementannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPoints()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/replacementannotation/#setPoints-java.util.List-com.groupdocs.annotation.models.Point--) defines the annotation positions as array of points
*   [setTextToReplace()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/replacementannotation/#setTextToReplace-java.lang.String-) defines the replacement text   
     

To add a replacement annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [ReplacementAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/replacementannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [ReplacementAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/replacementannotation) class.
4.  Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream. 

  

The following code snippet shows how to add [ReplacementAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/replacementannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding text replacement annotation.

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

    // Create an instance of ReplacementAnnotation class and set options
    ReplacementAnnotation replacement = new ReplacementAnnotation();
    replacement.setCreatedOn(Calendar.getInstance().getTime());
    replacement.setFontColor(65535);
    replacement.setMessage("This is replacement annotation");
    replacement.setOpacity(0.7);
    replacement.setPageNumber(0);
    replacement.setPoints(points);
    replacement.setReplies(replies);
    replacement.setTextToReplace("replaced text");
    
    // Add annotation and save to file
    annotator.add(replacement);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}