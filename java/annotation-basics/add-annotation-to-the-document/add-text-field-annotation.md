---
id: add-text-field-annotation
url: annotation/java/add-text-field-annotation
title: Add text field annotation
weight: 13
description: "The page describes how to add text field annotation to a document programmatically using GroupDocs.Annotation for Java."
keywords: text field annotation, add
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
        description: Learn how to add text field annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Annotation class declaration 
          text: Create an instance of TextFieldAnnotation class.
        - name: Specify annotation options
          text: In the TextFieldAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name TextFieldAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Text field annotation adds a rectangle with a text as shown in the picture below:

![](/annotation/java/images/add-text-field-annotation.png)

You can use the following methods to set the properties of the [TextFieldAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation) class:

*   [setBackgroundColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setBackgroundColor-java.lang.Integer-) defines the area background color
*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position at the document page
*   [setText()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setText-java.lang.String-) defines the text to place in the rectangle
*   [setFontColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setFontColor-java.lang.Integer-) defines the color of the text
*   [setFontFamily()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setFontFamily-java.lang.String-) defines the name of the text font
*   [setFontSize()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setFontSize-java.lang.Double-) defines the size of the text font
*   [setOpacity()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [setPenStyle()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setPenStyle-java.lang.Byte-) defines the frame line style (solid, dash, dot etc.)
*   [setPenWidth()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setPenWidth-java.lang.Byte-) - defines frame line width in pixels
*   [setPenColor()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setPenColor-java.lang.Integer-) defines the frame color
*   [setTextHorizontalAlignment()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation/#setTextHorizontalAlignment-java.lang.Integer-) defines the text horizontal alignment

To add a text field annotation, follow these steps: 

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [TextFieldAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [TextFieldAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation) class.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.  

The following code snippet shows how to add [TextFieldAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/textfieldannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding text field annotation.

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

    // Create an instance of TextFieldAnnotation class and set options
    TextFieldAnnotation textField = new TextFieldAnnotation();
    textField.setBackgroundColor(65535);
    textField.setBox(new Rectangle(100, 100, 100, 100));
    textField.setCreatedOn(Calendar.getInstance().getTime());
    textField.setText("Some text");
    textField.setFontColor(65535);
    textField.setFontSize((double)12);
    textField.setMessage("This is text field annotation");
    textField.setOpacity(0.7);
    textField.setPageNumber(0);
    textField.setPenStyle(PenStyle.Dot);
    textField.setPenWidth((byte) 3);
    textField.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(textField);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}
