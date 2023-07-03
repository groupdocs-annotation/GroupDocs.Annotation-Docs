---
id: add-resource-redaction-annotation
url: annotation/java/add-resource-redaction-annotation
title: Add resource redaction annotation
weight: 11
description: "The page describes how to add resource redaction annotation to a document using GroupDocs.Annotation for Java."
keywords: resource redaction, add
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
        description: Learn how to add resource redaction annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements
        - name: Annotation class declaration. 
          text: Create an instance of ResourcesRedactionAnnotation class.
        - name: Specify annotation options 
          text: In the ResourcesRedactionAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ResourcesRedactionAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Resource redaction annotation fills black rectangle with fixed position to hide a text as shown in the picture below:

![](/annotation/java/images/add-resource-redaction-annotation.png)

You can use the following methods to set the properties of the [ResourcesRedactionAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) class:

*   [setBox()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/resourcesredactionannotation/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation on the page

To add a resource redaction annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [ResourceRedactionAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [ResourceRedactionAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) class.
4.  Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream. 

The following code snippet shows how to add [ResourcesRedactionAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding resources redaction annotation.

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

    // Create an instance of ResourcesRedactionAnnotation class and set options
    ResourcesRedactionAnnotation resourcesRedaction = new ResourcesRedactionAnnotation();
    resourcesRedaction.setBox(new Rectangle(100, 100, 100, 100));
    resourcesRedaction.setCreatedOn(Calendar.getInstance().getTime());
    resourcesRedaction.setMessage("This is resources redaction annotation");
    resourcesRedaction.setPageNumber(0);
    resourcesRedaction.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(resourcesRedaction);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}