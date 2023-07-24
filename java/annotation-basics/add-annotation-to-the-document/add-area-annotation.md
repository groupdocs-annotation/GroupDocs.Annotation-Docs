---
id: add-area-annotation
url: annotation/java/add-area-annotation
title: Add area annotation
weight: 1
description: "The page describes how to add area annotation to a document using GroupDocs.Annotation for Java."
keywords: area annotation, add annotation
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
        description: Learn how to add area annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of AreaAnnotation class.
        - name: Specify annotation options 
          text: In the AreaAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name AreaAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Area annotation allows you to mark up a rectangle area within the document page and annotate it as shown in the picture below. 

![](/annotation/java/images/add-area-annotation.png)

You can use the following methods to set the properties of the [AreaAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/) class:
https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/#setBackgroundColor-java.lang.Integer-
*   [setBackgroundColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/#setBackgroundColor-java.lang.Integer-) defines the area background color
*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position at the document page
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPenColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/#setPenColor-java.lang.Integer-) defines the frame color
*   [setPenStyle()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/#setPenStyle-java.lang.Byte-) defines the frame line style (solid, dash, dot etc.)
*   [setPenWidth()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/#setPenWidth-java.lang.Byte-) defines the frame line width in pixels

To add an area annotation to document, follow these steps:  

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [AreaAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [AreaAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.  

The following code snippet shows how to add [AreaAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/areaannotation/) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
// This example demonstrates adding area annotation.

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

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");
try {
    // Create an instance of AreaAnnotation class and set options
    AreaAnnotation area = new AreaAnnotation();
    area.setBackgroundColor(65535);
    area.setBox(new Rectangle(100, 100, 100, 100));
    area.setCreatedOn(Calendar.getInstance().getTime());
    area.setMessage("This is area annotation");
    area.setOpacity(0.7);
    area.setPageNumber(0);
    area.setPenColor(65535);
    area.setPenStyle(PenStyle.Dot);
    area.setPenWidth((byte) 3);
    area.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(area);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}
