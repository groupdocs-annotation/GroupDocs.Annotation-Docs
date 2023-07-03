---
id: add-polyline-annotation
url: annotation/java/add-polyline-annotation
title: Add polyline annotation
weight: 9
description: "The page describes how to add polyline annotation to a document using GroupDocs.Annotation for Java."
keywords: polyline, annotation, add
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
        description: Learn how to add polyline annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of PolylineAnnotation class.
        - name: Specify annotation options 
          text: In the PolylineAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name PolylineAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Polyline annotation allows you to draw shapes and freehand lines as shown in the picture below: 

![](/annotation/java/images/add-polyline-annotation.png)

You can use the following methods to set the properties of the [PolylineAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation) class:

*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position on the page
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPenColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation/#setPenColor-java.lang.Integer-) defines the frame color
*   [setPenStyle()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation/#setPenStyle-java.lang.Byte-) defines the frame line style (solid, dash, dot etc.)
*   [setPenWidth()](https://reference.groupdocs.comhttps://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation/#setPenWidth-java.lang.Byte-) defines the frame line width in pixels
*   [setSvgPath()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation/#setSvgPath-java.lang.String-) defines the SVG path that describes shape

To add a polyline annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [PolylineAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [PolylineAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation) class.
4.  Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream. 

The following code snippet shows how to add [PolylineAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/polylineannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding polyline annotation.

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

    // Create an instance of AreaAnnotation class and set options
    PolylineAnnotation polyline = new PolylineAnnotation();
    polyline.setBox(new Rectangle(250, 35, 102, 12));
    polyline.setCreatedOn(Calendar.getInstance().getTime());
    polyline.setMessage("This is polyline annotation");
    polyline.setOpacity(0.7);
    polyline.setPageNumber(0);
    polyline.setPenColor(65535);
    polyline.setPenStyle(PenStyle.Dot);
    polyline.setPenWidth((byte) 3);
    polyline.setReplies(replies);
    polyline.setSvgPath("M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0");
    
    // Add annotation and save to file
    annotator.add(polyline);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}