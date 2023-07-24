---
id: add-watermark-annotation
url: annotation/java/add-watermark-annotation
title: Add watermark annotation
weight: 16
description: "The page describes how to add watermark annotation to a document using GroupDocs.Annotation for Java."
keywords: watermark, annotation, add
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
        description: Learn how to add watermark annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of WatermarkAnnotation class.
        - name: Specify annotation options
          text: In the WatermarkAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name WatermarkAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Watermark annotation allows you to add a text watermark as shown in the picture below:

![](/annotation/java/images/add-watermark-annotation.png)

You can use the following methods to set the properties of the [WatermarkAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation) class:

*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position at the document page
*   [setText()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setText-java.lang.String-) defines the watermark text
*   [setFontColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setFontColor-java.lang.Integer-) defines the color of the annotation text
*   [setFontFamily()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setFontFamily-java.lang.String-) defines the font of the annotation text
*   [setFontSize()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setFontSize-java.lang.Double-) defines the text font size
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setAngle()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setAngle-java.lang.Double-) defines the watermark text angle
*   [setVerticalAlignment()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setVerticalAlignment-java.lang.Integer-)  defines the vertical alignment
*   [setHorizontalAlignment()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setHorizontalAlignment-java.lang.Integer-) defines the horizontal alignment
*   [setAutoScale()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation/#setAutoScale-java.lang.Boolean-) sets the watermark size  depending on the word length and the page size

To add a watermark annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [WatermarkAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [WatermarkAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

  

The following code snippet shows demonstrates how to add [WatermarkAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/watermarkannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding watermark annotation.

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

    // Create an instance of WatermarkAnnotation class and set options
    WatermarkAnnotation watermark = new WatermarkAnnotation();
    watermark.setAngle((double) 75);
    watermark.setBox(new Rectangle(200, 200, 100, 50));
    watermark.setCreatedOn(Calendar.getInstance().getTime());
    watermark.setText("Watermark");
    watermark.setFontColor(65535);
    watermark.setFontSize((double) 12);
    watermark.setMessage("This is watermark annotation");
    watermark.setOpacity(0.7);
    watermark.setPageNumber(0);
    watermark.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(watermark);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}.