---
id: add-highlight-annotation
url: annotation/java/add-highlight-annotation
title: Add highlight annotation
weight: 5
description: "Learn what is a highlight annotation and how to add it to a document programmatically using GroupDocs.Annotation for Java."
keywords: What is a highlight annotation, how to add annotation, add highlight annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: Highlight annotation in document using Java
        description: Add highlight annotation to pdfs, words and other documents natively on mac, windows or ubuntu with high performance using Java language and GroupDocs.Annotation for Java APIs
        productCode: annotation
        productPlatform: java 
    showVideo: True
    howTo:
        name: How to add highlight annotation and notes to document in Java
        description: Learn how to add highlight annotation for mark up words, pdf or other document in Java step by step
        steps:
        - name: Load pdf, word or other document file
          text: Create an instance of Annotator class and pass source document file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Set data for highlight annotation
          text: Create an instance of HighlightAnnotation class and add data for highlight annotation.
        - name: Add annotation to document and save result
          text: Call Annotator class Add method and pass the HighlightAnnotation object from the previous step as parameter then call Save method from Annotator class and pass the output filename as parameter.
---
**Highlight** annotation highlights and comments selected text  like shown at the picture below. 

![](annotation/java/images/add-highlight-annotation.png)

There is an ability to specify the next fields for [HighlightAnnotation](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation) type:
*   [BackgroundColor](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation#getBackgroundColor()) - describes area background color;
*   [FontColor](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation#getFontColor())  - color of annotation text;
*   [Opacity](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation#getOpacity()) - allows to set annotation opacity;
*   [Points](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation#getPoints()) - annotation positions set by array of points.
    

Follow these steps to add Highlight annotation to document:
*   Instantiate [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object with input document path or stream;
*   Instantiate [HighlightAnnotation](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation) object with desired properties (position, page number, etc);
*   Call [add](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)) method and pass [HighlightAnnotation](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation) object;
*   Call [save](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#save(java.io.InputStream)) method with resultant document path or stream.

The following code demonstrates how to add [HighlightAnnotation](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation) to the document:

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-add-text-highlight-annotation.java" >}}

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/java/developer-guide/advanced-usage/_index.md" >}}).

### GitHub Examples
You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Annotation for .NET examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
*   [GroupDocs.Annotation for Java examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java)
*   [Document Annotation for .NET MVC UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC)
*   [Document Annotation for .NET App WebForms UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms)
*   [Document Annotation for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Dropwizard)
*   [Document Annotation for Java Spring UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Spring)

### Free Online App
Along with full-featured Java library we provide simple, but powerful free Apps.  
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
