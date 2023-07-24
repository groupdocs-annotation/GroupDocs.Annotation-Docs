---
id: add-link-annotation
url: annotation/java/add-link-annotation
title: Add link annotation
weight: 7
description: "The page describes how to add link annotation to a document using GroupDocs.Annotation for Java."
keywords: link annotation,add
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
        description: Learn how to add link annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of LinkAnnotation class.
        - name: Specify annotation options 
          text: In the LinkAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name LinkAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Link annotation adds a hyperlink to document as shown in the picture below:

![](/annotation/java/images/add-link-annotation.png)

You can use the following methods to set the properties of the [LinkAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/linkannotation) class:

*   [setUrl()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/linkannotation/#setUrl-java.lang.String-) defines link to a web resource
*   [setPoints()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/linkannotation/#setPoints-java.util.List-com.groupdocs.annotation.models.Point--) defines the annotation positions as an array of points.  
    
To add a link annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [LinkAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/linkannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [LinkAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/linkannotation) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows how to add [LinkAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/linkannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding link annotation.

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

    java.util.List<Reply> replies = Arrays.asList(reply1, reply2);
    
    List<Point> points = Arrays.asList(new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650));                
    
    // Create an instance of LinkAnnotation class and set options
    LinkAnnotation link = new LinkAnnotation();
    link.setCreatedOn(Calendar.getInstance().getTime());
    link.setMessage("This is link annotation");
    link.setOpacity(0.7);
    link.setPageNumber(0);
    
    link.setPoints(points);               
    
    link.setReplies(replies);
    link.setUrl("https://www.google.com");
    
    // Add annotation and save to file
    annotator.add(link);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}