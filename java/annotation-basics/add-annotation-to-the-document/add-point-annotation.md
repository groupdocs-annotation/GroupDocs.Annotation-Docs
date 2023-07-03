---
id: add-point-annotation
url: annotation/java/add-point-annotation
title: Add point annotation
weight: 8
description: "The page describes how to add point annotation to a document using GroupDocs.Annotation for Java."
keywords: point annotation, add
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
        description: Learn how to add point annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of PointAnnotation class.
        - name: Specify annotation options 
          text: In the PointAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name PointAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Point annotation sticks comments to any point in a document as shown in the picture below:

![](/annotation/java/images/add-point-annotation.png)

You can use the following methods to set the properties of the [PointAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/pointannotation) class:

*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/pointannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position on the page
    

To add a point annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [PointAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/pointannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [PointAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/pointannotation) class.
4.  Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream. 

The following code snippet shows how to add [PointAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/pointannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding point annotation.

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

    // Create an instance of PointAnnotation class and set options
    PointAnnotation point = new PointAnnotation();
    point.setBox(new Rectangle(100, 100, 0, 0));
    point.setCreatedOn(Calendar.getInstance().getTime());
    point.setMessage("This is point annotation");
    point.setPageNumber(0);
    point.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(point);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}