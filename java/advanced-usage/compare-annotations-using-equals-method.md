---
id: comparing-annotations-using-equals-method
url: annotation/java/comparing-annotations-using-equals-method
title: Compare annotations
weight: 6
description: "The page describes how to compare annotations."
keywords: compare, annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
    showVideo: False
    howTo:
        name: How to compare annotation using equals method
        description: Learn how to compare annotation using equals method step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Get annotation
          text: Get all annotations to created variable.
        - name: Annotation class declaration          
          text: Create an instance of ImageAnnotation class.
        - name: Specify annotation options 
          text: In the ImageAnnotation class constructor, pass parameters.
        - name: Compare annotations
          text: With a foreach loop, compare all annotations with yours.
toc: True
---

GroupDocs.Annotation v21.7. and later allows you to compare annotations using the `Equals` method.

The following code snippet shows how to compare annotations:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to update annotation.

// Create an instance of Annotator class
try (Annotator annotator = new Annotator("annotated_file.pdf")) {
    List<AnnotationBase> annotations = annotator.get();
    
    // Create an instance of the ImageAnnotation class and add options
    ImageAnnotation imageAnnotation = new ImageAnnotation();
    imageAnnotation.setBox(new Rectangle(100, 100, 100, 100));
    imageAnnotation.setOpacity(0.7);
    imageAnnotation.setPageNumber(0);
    imageAnnotation.setImagePath("www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png");
    imageAnnotation.setAngle(100.0);

    for(int i = 0; i < annotations.size(); i++) {
        // Compare annotations
        if (imageAnnotation.equals(annotations.get(i))) {
                // Do some stuff here...
        }
    }
}
```
{{< /tab >}}
{{< /tabs >}}
