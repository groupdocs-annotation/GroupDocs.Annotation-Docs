---
id: filtering-annotation-types
url: annotation/java/filtering-annotation-types
title: Filtering annotations by type on saving document
weight: 1
description: "This page describes how to filter annotation by type on saving file using GroupDocs.Annotation for Java API."
keywords: specific annotation types, save annotations
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
          text: Create an instance of AreaAnnotation class and EllipseAnnotation class.
        - name: Specify annotation options 
          text: In the AreaAnnotation class and EllipseAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: In the .Add() method, create a new instance of the annotation collections and pass the annotation names to it.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file and class SaveOptions with the annotation type you want to save.
toc: True
---
To save only annotations of specific types, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [SaveOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/) class. Call the [setAnnotationType()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/#setAnnotationTypes-int-) method and specify the annotation type(s) to save.
3.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method with the resultant document path or stream. Specify the [SaveOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/saveoptions/) class as a parameter.

The following code snippet shows how to save only pages with specific annotation type:

{{< tabs "example1">}}
{{< tab "Java" >}}
// This example demonstrates saving result document with specified annotations.

// Create an instance of Annotator class
Annotator annotator = new Annotator(Constants.ANNOTATED_BIG);
try {
    // Create an instance of AreaAnnotation class and set options
    AreaAnnotation area = new AreaAnnotation();
    area.setBox(new Rectangle(100, 100, 100, 100));
    area.setBackgroundColor(65535);
    area.setPageNumber(1);
    
    // Create an instance of EllipseAnnotation class and set options
    EllipseAnnotation ellipse = new EllipseAnnotation();
    ellipse.setBox(new Rectangle(100, 100, 100, 100));
    ellipse.setBackgroundColor(123456);
    ellipse.setPageNumber(4);
    
    List<AnnotationBase> tmp0 = new ArrayList<AnnotationBase>();
    tmp0.add(area);
    tmp0.add(ellipse);
    annotator.add(tmp0);
    
    SaveOptions tmp1 = new SaveOptions();
    tmp1.setAnnotationTypes(AnnotationType.Ellipse);
    
    // Add annotation and save to file
    annotator.save(outputPath, tmp1);
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}