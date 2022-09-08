---
id: how-to-add-or-remove-annotation-from-pdf-files
url: annotation/java/how-to-add-or-remove-annotation-from-pdf-files
title: How to Add or Remove Annotations from PDF files using Java
weight: 1
description: "Programmatically add and remove annotations from PDF files. Add arrow, rectangle annotations and more using Java API."
keywords: highlight PDF, add annotations in PDF, Annotate PDF, Remove annotations from PDF, 
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to add and remove annotations from PDF documents. Add arrow, rectangle annotations and more using Java API.
    showVideo: False
    howTo:
        name: How to add and remove annotations
        description: Learn how to add arrow and rectangle annotations to the PDF document
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Annotation class declaration
            text: Create an instance of ArrowAnnotation or AreaAnnotation class.
          - name: Specify annotation options 
            text: In the ArrowAnnotation or AreaAnnotation class constructor pass parameters.
          - name: Add annotation to the document
            text: Call method Add() on Annotator object and pass ArrowAnnotation or AreaAnnotation instance there.
          - name: Save document with annotation
            text: Call method Save() on Annotator object and pass output file destination there.
---

There was a time when we used to discuss document content and feedback in long email threads with multiple attachments and different file versions. Now we can simply use annotations to markup the document with messages and replies and send it. In this article, you will learn how to programmatically annotate PDF documents in Java with your application. Additionally, we will see how to remove annotations from PDF files using the same Java API.

### PDF Annotator Java API

To deal with annotations of your document and images within your Java applications, GroupDocs provides [GroupDocs.Annotation for Java](https://products.groupdocs.com/annotation/java). Using the API, you can add, remove, and extract annotations from **word-processing** documents, **spreadsheets**, **presentations**, **images**, **email messages**, Visio **drawings**, some **AutoCAD**, and **digital imaging formats** like **DICOM**. Furthermore, the API allows annotating PDF files. You may have a look at the documentation to know about the long list of [supported document formats for annotation](https://docs.groupdocs.com/annotation/java/supported-document-formats/).

### Download and Configure

GroupDocs hosts all Java APIs on [GroupDocs Repository](https://repository.groupdocs.com/). You can easily use [GroupDocs.Annotation for Java](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-annotation) API directly in your Maven projects with simple configurations.

### Specify GroupDocs Repository Configuration

First, you need to specify GroupDocs repository configuration/location in your Maven `pom.xml` as follows: 

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-installation-repository.xml" >}}

### Define GroupDocs.Annotation for Java API Dependency

Then define GroupDocs.Annotation for Java API dependency in your `pom.xml` as follows:

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-installation-dependency.xml" >}}

Let’s quickly jump to add some of the different kinds of annotations to the PDF document. As there are many different types of annotation, we may not cover all in this article. I will just mention them, and you may [learn about each annotation individually](https://docs.groupdocs.com/annotation/java/add-annotation-to-the-document/).

*   Area / Rectangle annotation
*   Arrow
*   Distance
*   Ellipse
*   Highlight
*   Link
*   Point
*   Polyline
*   Replacement
*   Resource Redaction
*   Strikeout
*   Text Field
*   Text Redaction
*   Underline
*   Watermark
    
Let’s start adding some of these in a PDF document.

### Add Arrow Annotation to PDF using Java

The following are the steps to add arrow annotation to a PDF document.

![Arrow Annotation](/annotation/java/images/add-arrow-annotation.png)

*   Load the PDF document using the [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) class.
*   Initialize arrow annotation using [ArrowAnnotation](https://apireference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/arrowannotation) class.
*   Set the position and size of the arrow using [Box](https://apireference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/arrowannotation/properties/box) property of ArrowAnnotation.
*   Add the created arrow annotation to the Annotator object.
*   Save the annotated PDF by providing the path using the [Save](https://apireference.groupdocs.com/annotation/java/groupdocs.annotation/annotator/methods/save) method.


The following code sample shows how to add arrow annotation to a PDF document using Java.

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-add-arrow-annotation.java" >}}

### Insert Rectangle or Area Annotation to PDF using Java

You can customize any annotation while adding it to the document. The following are the steps to add rectangle or area annotation to a PDF document with little more customizations. It is similar to adding Arrow annotation but uses **AreaAnnotation** class in place of **ArrowAnnotation**.

*   Load the PDF document using the [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) class.
*   Initialize rectangle annotation using [AreaAnnotation](https://apireference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/areaannotation) class.
*   Set the position and size of the rectangle using [Box](https://apireference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/areaannotation/properties/box) property of AreaAnnotation.
*   Set other properties like **PenColor**, **BackgroundColor**, **Opacity**, **PenStyle**, **PenWidth**, and even **Replies**.
*   Add the created rectangle annotation to the Annotator object.
*   Save the annotated PDF by providing the path using the [Save](https://apireference.groupdocs.com/annotation/java/groupdocs.annotation/annotator/methods/save) method.

![Rectangle or Area Annotation](/annotation/java/images/add-area-annotation.png)

The following code sample shows how to add rectangle/area annotation to a PDF document using Java.

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-add-area-annotation.java" >}}

We have only shown you 2 examples because all the other types of annotation work in a similar way. You can try and add all the other annotations yourself or by following our [detailed guides](https://docs.groupdocs.com/annotation/java/add-annotation-to-the-document/) related to every annotation we support.

### Remove Annotations from PDF in Java

The following steps show how to remove all the annotations from PDF files in Java.

*   Load the PDF document using the [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) class.
*   Initialize saving Options using [SaveOptions](https://apireference.groupdocs.com/annotation/java/groupdocs.annotation.options/saveoptions) class.
*   Set the annotation types to None.
*   Save the PDF file having all the annotations removed, by providing the path using the [save](https://apireference.groupdocs.com/annotation/java/groupdocs.annotation/annotator/methods/save) method.

The following Java code removes annotations from a PDF file.

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-remove-annotation-from-document.java" >}}

### Conclusion 

In short, you have learned how to add annotations to PDF within Java applications. Further, you have seen how to remove all the annotations from any PDF file. Now, you should be confident to build your own document annotator Java application. It can support different types of annotations using GroupDocs.Annotation for Java.

For more details, options, and examples, you can visit the [documentation](https://docs.groupdocs.com/annotation/java/) and the [GitHub](https://github.com/groupdocs-annotation) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/).
