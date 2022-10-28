---
id: add-replies-to-annotation
url: annotation/java/add-replies-to-annotation
title: Add replies to annotation
weight: 1
description: "Check this guide to learn how to add annotation replies when collaborate over document using GroupDocs.Annotation for Java API."
keywords: How to add annotation reply, add annotation reply, add reply, reply to annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: Add annotation replies to pdfs, words and other documents with Java
        description: Add annotation replies to document word, pdf and other docs natively on mac, windows or ubuntu with high performance using Java language and GroupDocs.Annotation for Java APIs
        productCode: annotation
        productPlatform: java 
    showVideo: True
    howTo:
        name: How to add annotation replies to document in Java 
        description: Learn how to add annotation replies to document in Java step by step
        steps:
        - name: Load source document file with replies
          text: Create an instance of Annotator class and pass source document file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Create new annotation replies
          text: Create an instance of Reply class and add data then create java List with Reply and add all replies to this list.
        - name: Add annotation replies
          text: Create an instance of AreaAnnotation (or other type of annotation) and call setUpdate method for add list with replies. 
        - name: Add annotation to document and save result 
          text: Call Annotator class Add method and pass the AreaAnnotation (or other type of annotation) object with updated replies from the previous step as parameter then call Save method from Annotator class and pass the output filename as parameter.
toc: True
---

[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/java) provides ability for several users to collaborate over document via annotation replies. Adding reply to an annotation via code is as easy as specifying reply content and related user object.  
Here are the steps to add annotation replies:

*   Instantiate [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object with input document path or stream;
*   Instantiate [User](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models/User) object;
*   Instantiate [Reply](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models/Reply) object(s);
*   Instantiate some of [AnnotationBase](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/AnnotationBase) implementation object;
*   Assign [User](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models/User) object to Reply.User property (or by default will be "Guest");
*   Assign [Reply](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models/Reply) object(s) to implementation of [AnnotationBase](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/AnnotationBase) object Replies property;
*   Call [add](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)) method of [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object with passed annotations;
*   Call [save](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#save(java.io.InputStream)) method with resultant document path or stream and [SaveOptions](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.options.export/SaveOptions) object;
    
The following code demonstrates how to add replies to annotation:

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-add-replies.java" >}}

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
