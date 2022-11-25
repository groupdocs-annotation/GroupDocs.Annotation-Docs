---
id: add-distance-annotation
url: annotation/java/add-distance-annotation
title: Add distance annotation
weight: 3
description: "Learn what is a distance annotation and how to add it to a document programmatically using GroupDocs.Annotation for Java."
keywords: What is a distance annotation, how to add annotation, add distance annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: Distance annotation in document using Java
        description: Add distance annotation to pdfs, words and other documents natively on mac, windows or ubuntu with high performance using Java language and GroupDocs.Annotation for Java APIs
        productCode: annotation
        productPlatform: java 
    showVideo: True
    howTo:
        name: How to add distance annotation and notes to document in Java
        description: Learn how to add distance annotation for mark up words, pdf or other document in Java step by step
        steps:
        - name: Load pdf, word or other document file
          text: Create an instance of Annotator class and pass source document file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Set data for distance annotation
          text: Create an instance of DistanceAnnotation class and add data for distance annotation.
        - name: Add annotation to document and save result
          text: Call Annotator class Add method and pass the DistanceAnnotation object from the previous step as parameter then call Save method from Annotator class and pass the output filename as parameter.
toc: True
---

**Distance annotation** measures a distance between objects in a document like shown at the picture below. 

![](/annotation/java/images/add-distance-annotation.png)

There is an ability to specify the next fields for [DistanceAnnotation](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation) type:
*   [Box](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation#getBox()) - defines annotation position at document page;
*   [Opacity](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation#getOpacity()) - allows to set annotation opacity;
*   [PenColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation#getPenColor()) - defines frame color;
*   [PenStyle](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation#getPenStyle()) - defines frame line style (solid, dash, dot etc.);
*   [PenWidth](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation#getPenWidth()) -  defines frame line width in pixels.
    

  
Follow these steps to add Distance annotation to document:
*   Instantiate [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object with input document path or stream;
*   Instantiate [DistanceAnnotation](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation) object with desired properties (position, page number, etc);
*   Call [add](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)) method and pass [DistanceAnnotation](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation) object;
*   Call [save](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#save(java.io.InputStream)) method with resultant document path or stream.
    

The following code demonstrates how to add [DistanceAnnotation](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation) to the document:

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-add-distance-annotation.java" >}}

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
