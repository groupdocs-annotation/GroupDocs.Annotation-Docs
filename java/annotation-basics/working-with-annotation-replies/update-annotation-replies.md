---
id: update-annotation-replies
url: annotation/java/update-annotation-replies
title: Update annotation replies
weight: 3
description: "The page describes how to update annotation replies when collaborate over document using GroupDocs.Annotation for Java API."
keywords: update annotation reply, change reply, reply to annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
    showVideo: False
    howTo:
        name: How to update replies to annotation
        description: Learn how to update replies annotation step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Obtain annotations collection from document
        - name: Update reply 
          text: set the Comment parameter of the AnnotationBase class
        - name: Update document with annotations
          text: Call Annotator class .Update() method.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/java) provides an ability to update annotation replies by accessing them using the [Replies](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/annotationbase/#getReplies--) collection.

To update annotation replies, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Call the [get()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#get--) method of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class to get collection of the document annotations.
3.   Access desired reply object via [getReplies()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/annotationbase/#getReplies--) method collection by its index (zero-based) and update its properties as needed.
4.   Call the [update](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#update-java.util.List-com.groupdocs.annotation.models.annotationmodels.AnnotationBase--) method of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify annotations.
5.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream and the [SaveOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/) class.
    

The following code snippet shows how to update reply by index: 

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to update annotation.

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");
try {
    // Create an instance of Reply class and add comments
    Reply reply1 = new Reply();
    reply1.setComment("Original first comment");
    reply1.setRepliedOn(Calendar.getInstance().getTime());

    Reply reply2 = new Reply();
    reply2.setComment("Original second comment");
    reply2.setRepliedOn(Calendar.getInstance().getTime());

    java.util.List<Reply> replies =  new ArrayList<Reply>();
    replies.add(reply1);
    replies.add(reply2);

    // Create an instance of AreaAnnotation class and set options
    AreaAnnotation original = new AreaAnnotation();
    original.setId(1);
    original.setBackgroundColor(65535);
    original.setBox(new Rectangle(100, 100, 100, 100));
    original.setCreatedOn(Calendar.getInstance().getTime());
    original.setMessage("This is original annotation");
    original.setReplies(replies);
    
    // Add original annotation
    annotator.add(original);
    
    // Save to file
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
LoadOptions tmp0 = new LoadOptions();

// Open annotated document
Annotator annotator1 = new Annotator("outputPath", tmp0);
try {
    // Create an instance of Reply class and add comments
    Reply reply1 = new Reply();
    reply1.setComment("Updated first comment");
    reply1.setRepliedOn(Calendar.getInstance().getTime());

    Reply reply2 = new Reply();
    reply2.setComment("Updated second comment");
    reply2.setRepliedOn(Calendar.getInstance().getTime());

    java.util.List<Reply> replies =  new ArrayList<Reply>();
    replies.add(reply1);
    replies.add(reply2);

    // Suggest we want change some properties of existed annotation
    AreaAnnotation updated = new AreaAnnotation();
    updated.setId(1);
    updated.setBackgroundColor(255);
    updated.setBox(new Rectangle(0, 0, 50, 200));
    updated.setCreatedOn(Calendar.getInstance().getTime());
    updated.setMessage("This is updated annotation");
    updated.setReplies(replies);
    
    // update annotation
    annotator1.update(updated);
    
    // Save to file
    annotator1.save(outputPath);
} finally {
    if (annotator1 != null) {
        annotator1.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}