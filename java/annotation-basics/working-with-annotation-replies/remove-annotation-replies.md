---
id: remove-annotation-replies
url: annotation/java/remove-annotation-replies
title: Remove annotation replies
weight: 2
description: "The page describes how to remove all or specific annotation replies when collaborate over document using GroupDocs.Annotation for Java API."
keywords: remove annotation reply, reply to annotation, remove annotation comment
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
    showVideo: False
    howTo:
        name: How to remove annotation replies
        description: Learn how to remove annotation replies step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Obtain annotations collection from document
        - name: Remove reply 
          text: Call AnnotationBase class .RemoveAt() method.
        - name: Update document with annotations
          text: Call Annotator class .Update() method.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
You can remove specific or all replies using the [GroupDocs.Annotation](https://products.groupdocs.com/annotation/java) API. To do this, remove the appropriate items from the `List<T>` collection. 

To delete an annotation reply (replies), follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Call the [get()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#get--) method of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class to get collection of document annotations.
3.   Access the appropriate annotation and remove a reply in a suitable way:
    *   call the `annotations.get(index).getReplies().remove(index)` method. Specify approptiate parameters;
    *   call the [AnnotationBase.getReplies()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/annotationbase/#getReplies--) method and remove replies that match desired criteria.
4.   Call the [update](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#update-java.util.List-com.groupdocs.annotation.models.annotationmodels.AnnotationBase--) method of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the annotations collection.
5.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.
    

## Remove specific annotation reply 

The following code snippet shows how to remove annotation reply by its index:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to remove replies from annotated document by reply Id.

LoadOptions tmp0 = new LoadOptions();

// NOTE: Input document already contain annotations with replies
final Annotator annotator = new Annotator("inputPath", tmp0);
try {
    // Obtain annotations collection from document
    List<AnnotationBase> annotations = annotator.get();

    // Remove reply with Id = 4
    annotations.get(0).getReplies().remove(4);

    // Update and save changes
    annotator.update(annotations);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}

## Remove annotation replies by criteria

The following code snippet shows how to remove replies that match some criteria:

{{< tabs "example2">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to remove replies from annotated document by user name.

LoadOptions tmp0 = new LoadOptions();

// NOTE: Input document already contain annotations with replies
Annotator annotator = new Annotator("inputPath", tmp0);
try {
    // Obtain annotations collection from document
    List<AnnotationBase> annotations = annotator.get();

    // Remove all replies where author name is "Tom"           
    for(int i = 0; i < annotations.get(0).getReplies().size(); i++) {
        if(annotations.get(0).getReplies().get(i).getUser().getName().toString().equals("Tom")) {
            annotations.get(0).getReplies().remove(i);
        }
    }

    // Update and save changes
    annotator.update(annotations);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}
