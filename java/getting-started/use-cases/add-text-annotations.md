---
id: how-to-add-text-annotations-to-pdf-file
url: annotation/java/how-to-add-text-annotations-to-pdf-file
title: How to Add Text Annotations to PDF files using Java
weight: 2
description: "Programmatically add text annotations to PDF files. Add text field and strikeout annotations using Java API."
keywords: highlight PDF, add annotations in PDF, annotate PDF, strikeout text for PDF
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to add text annotations to PDF documents using Java API.
    showVideo: False
    howTo:
        name: How to add text annotations
        description: Learn how to add text field and strikeout annotations to the PDF document
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Annotation class declaration
            text: Create an instance of TextFieldAnnotation or StrikeoutAnnotation class.
          - name: Specify annotation options 
            text: In the TextFieldAnnotation or StrikeoutAnnotation class constructor pass parameters.
          - name: Add annotation to the document
            text: Call method Add() on Annotator object and pass TextFieldAnnotation or StrikeoutAnnotation instance there.
          - name: Save document with annotation
            text: Call method Save() on Annotator object and pass output file destination there.
toc: True
---

## Text annotations

PDF is a good way to share documents with people. It guarantees you that your document looks on any computer exactly the same as it is on yours. But working with documents may sometimes require an ability to manipulate with a text. To do it programmatically you can use our Annotation API for Java. We support a various text annotations, such as: 

* [Highlight annotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation)
* [Link annotation](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/linkannotation)
* [Replacement annotation](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/replacementannotation)
* [Strikeout annotation](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/strikeoutannotation)
* [Text field annotation](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/textfieldannotation)
* [Text redaction annotation](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/textredactionannotation)
* [Squiggly annotation](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/squigglyannotation)
* [Underline annotation](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/underlineannotation)

In this article we will cover just a few of them - highlight and strikeout annotations. All others works in exactly the same way.

### Highlight annotation 

**Highlight** annotation highlights and comments selected text. This is a good way to "highlight" an import text, to bring it to the user's attention. Highlighting is used everywhere, so this is unquestionably text annotation number one.

![](/annotation/java/images/add-highlight-annotation.png)

You have ability to specify the next properties for [HighlightAnnotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) type:

*   [BackgroundColor](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/areaannotation/properties/backgroundcolor) - describes annotation background color;
*   [FontColor](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/linkannotation/properties/fontcolor) - color of annotation text;
*   [Opacity](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) - allows to set annotation opacity;
*   [Points](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/linkannotation/properties/points) - annotation positions set by array of points.

Follow these steps to add Highlight annotation to document:

*   Instantiate [Annotator](https://reference.groupdocs.com/java/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [HighlightAnnotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://reference.groupdocs.com/java/annotation/groupdocs.annotation/annotator/methods/add) method and pass [HighlightAnnotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) object;
*   Call [Save](https://reference.groupdocs.com/java/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.  
      

The following code demonstrates how to add [HighlightAnnotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) to the document:

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-add-text-highlight-annotation.java" >}}

### Strikeout annotation

**Strikeout** annotation marks text fragment with a strikethrough styling. When you receive a document for review and find errors or inconsistencies in it, it is very important to be able to draw the author's attention to them. We recommend to you strikeout annotation for these purposes. Whenever the highlight annotation draws attention to the correct and important parts of the document, the strikeout annotation is usually used to cross out the wrong and unimportant parts of the document. You can check an example below. 

![](/annotation/java/images/add-strikeout-annotation.png)

There is an ability to specify the next properties for [StrikeoutAnnotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/strikeoutannotation) type:

*   [FontColor](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/strikeoutannotation/properties/fontcolor) – color of annotation text;
*   [Opacity](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) – allows to set annotation opacity;
*   [Points](https://reference.groupdocs.com/annotation/java/groupdocs.annotation.models.annotationmodels/strikeoutannotation/properties/points) – annotation positions set by array of points.  
      


Follow these steps to add Strikeout annotation to document:

*   Instantiate [Annotator](https://reference.groupdocs.com/java/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [StrikeoutAnnotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/strikeoutannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://reference.groupdocs.com/java/annotation/groupdocs.annotation/annotator/methods/add) method and pass [StrikeoutAnnotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/strikeoutannotation) object;
*   Call [Save](https://reference.groupdocs.com/java/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.
 


The following code demonstrates how to add [StrikeoutAnnotation](https://reference.groupdocs.com/java/annotation/groupdocs.annotation.models.annotationmodels/strikeoutannotation) to the document:

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-add-text-strikeout-annotation.java" >}}

## Conclusion

In short, we have learned how to add text annotations to a PDF file within Java applications. We have introduced all the text annotations that our API supports and illustrated how and when to use them with an example. Now, you should be confident to build your own document annotator Java application. 

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/java/developer-guide/advanced-usage/_index.md" >}}).
    

### Free Online App
Along with full-featured Java library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
