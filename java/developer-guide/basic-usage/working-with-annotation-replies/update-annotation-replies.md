---
id: update-annotation-replies
url: annotation/java/update-annotation-replies
title: Update annotation replies
weight: 3
description: "Check this guide to learn how to update annotation replies when collaborate over document using GroupDocs.Annotation for Java API."
keywords: How to change or remove annotation reply, update annotation reply, remove reply, reply to annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: Update annotation replies in pdfs, words and other documents with Java
        description: Update annotation replies in document word, pdf and other docs natively on mac, windows or ubuntu natively with high performance using Java language and GroupDocs.Annotation for Java APIs
        productCode: annotation
        productPlatform: java 
    showVideo: True
    howTo:
        name: How to update annotation replies in document in Java 
        description: Learn how to update annotation replies in document in Java step by step
        steps:
        - name: Load source document file with replies
          text: Create an instance of Annotator class and pass source document file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Create new replies
          text: Create an instance of Reply class and add data then create java List with Reply and add all replies to this list.
        - name: Update annotation replies
          text: Create an instance of AreaAnnotation (or other type of annotation) and call setUpdate method for add list with replies.
        - name: Add annotation to document and save result 
          text: Call Annotator class Add method and pass the AreaAnnotation (or other type of annotation) object then call Save method from Annotator class and pass the output filename as parameter.
---
[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/java) provides and ability to programmatically update annotation replies by accessing them by their index inside [Replies](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/AnnotationBase#getReplies()) collection.

Here is a steps to update annotation reply (considered that we already have some reply added to annotation)
*   Instantiate [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object with input document path or stream with instantiated [LoadOptions](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.options/LoadOptions) with *ImportAnnotations = true;*
*   Call [get](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#get()) method of [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object and import annotations;
*   Access desired reply object via [getReplies](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/AnnotationBase#getReplies()) method collection by its index (zero-based) and update its properties as needed;
*   Call [update](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#update(java.util.List)) method of Annotator object with passed annotations;
*   Call [save](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#save(java.io.InputStream)) method with resultant document path or stream and [SaveOptions](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.options.export/SaveOptions) object;

The following code demonstrates how to update reply by index:

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-update-annotation.java" >}}

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
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online [**GroupDocs Annotation App**](https://products.groupdocs.app/annotation).
