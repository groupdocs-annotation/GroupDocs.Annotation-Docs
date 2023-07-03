---
id: add-distance-annotation
url: annotation/java/add-distance-annotation
title: Add distance annotation
weight: 3
description: "The page describes how to add distance annotation to a document using GroupDocs.Annotation for Java."
keywords: distance annotation, add annotation
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
        description: Learn how to add distance annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of DistanceAnnotation class.
        - name: Specify annotation options 
          text: In the DistanceAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name DistanceAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Distance annotation shows a distance between objects in a document as shown in the picture below: 

![](/annotation/java/images/add-distance-annotation.png)

You can use the following methods to set the properties of the [DistanceAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation) class:

*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines annotation position on a page
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPenColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation/#setPenColor-java.lang.Integer-) defines the annotation color
*   [setPenStyle()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation/#setPenStyle-java.lang.Byte-) defines the annotation line style (solid, dash, dot etc.)
*   [setPenWidth()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation/#setPenWidth-java.lang.Byte-) defines the line width in pixels

  
To add a distance annotation to document, follow these steps:  

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [DistanceAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation) class. Set the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [DistanceAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.  
      
The following code snippet shows how to add [DistanceAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/distanceannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding distance annotation.

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

    // Create an instance of DistanceAnnotation class and set options
    DistanceAnnotation distance = new DistanceAnnotation();
    distance.setBox(new Rectangle(200, 150, 200, 30));
    distance.setCreatedOn(Calendar.getInstance().getTime());
    distance.setMessage("This is distance annotation");
    distance.setOpacity(0.7);
    distance.setPageNumber(0);
    distance.setPenColor(65535);
    distance.setPenStyle(PenStyle.Dot);
    distance.setPenWidth((byte) 3);
    distance.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(distance);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}
