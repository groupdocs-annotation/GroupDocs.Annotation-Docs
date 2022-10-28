---
id: remove-annotation-replies
url: annotation/java/remove-annotation-replies
title: Remove annotation replies
weight: 2
description: "Check this guide to learn how to remove all or specific annotation replies when collaborate over document using GroupDocs.Annotation for Java API."
keywords: How to remove annotation reply, remove annotation reply, remove reply, reply to annotation, remove annotation comment
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: Remove annotation replies from pdfs, words and other documents with Java
        description: Remove annotation replies from document word, pdf and other docs natively on mac, windows or ubuntu with high performance using Java language and GroupDocs.Annotation for Java APIs
        productCode: annotation
        productPlatform: java 
    showVideo: True
    howTo:
        name: How to remove annotation replies from document in Java
        description: Learn how to remove annotation replies from document in Java step by step
        steps:
        - name: Load source document file with replies
          text: Create an instance of Annotator class and pass source document file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Get annotations and remove reply
          text: Get annotations from Annotator class and specify which reply need to delete by index or user name.
        - name: Remove annotation replies from document and save result
          text: Call Annotator class Update method and pass the AreaAnnotation (or other type of annotation) object with removed replies from the previous step as parameter then call Save method from Annotator class and pass the output filename as parameter.
toc: True
---

There is a quick and convenient way to remove specific or even all replies for some document annotation using **[GroupDocs.Annotation](https://products.groupdocs.com/annotation/java)** API. It is as easy as removing items from generic [List<T>](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1) collection. In common case you have to follow these steps to delete replies:

*   Instantiate [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object with input document path or stream
*   Call [get](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#get()) method of [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object and obtain collection of document annotations;
*   Access desired annotation object and remove reply in a most suitable way:
    *   Call *annotations.get(index).getReplies().remove(index)* method with desired parameters;
    *   Call [AnnotationBase.getReplies()](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.models.annotationmodels/AnnotationBase#getReplies()) and remove replies that match desired criteria;
*   Call [update](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#update(java.util.List)) method of [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object and pass annotations collection into it;
*   Call [save](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#save(java.lang.String)) method with resultant document path or stream;
    

## Remove specific annotation reply 

The easiest way for removing specific annotation reply is to delete by its index inside Replies collection. The following code sample demonstrates how to remove first annotation reply:

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-remove-replies-by-id.java" >}}

## Remove annotation replies by criteria

The following code demonstrates how to remove replies that were added by user with name "Tom":

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-remove-replies-by-user-name.java" >}}