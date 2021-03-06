---
id: generate-document-pages-preview
url: annotation/java/generate-document-pages-preview
title: Generate document pages preview
weight: 3
description: ""
keywords: 
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: Generate document pages preview
        description: Generate document pages preview for pdfs, words and other documents natively on mac, windows or ubuntu with high performance using Java language and GroupDocs.Annotation for Java APIs
        productCode: annotation
        productPlatform: java 
    showVideo: True
    howTo:
        name: How to generate document pages preview in Java
        description: Learn how to generate document pages preview for words, pdf or other document in Java step by step
        steps:
        - name: Load pdf, word or other document file
          text: Create an instance of Annotator class and pass source document file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Add options for preview annotation
          text: Create an instance of PreviewOptions class and add information for preview annotation.
        - name: Generate preview
          text: Call Annotator class generatePreview method for Generate preview for pdfs, words, cells, images, diagrams.
---
**[GroupDocs.Annotation](https://products.groupdocs.com/annotation/java)** allows to generate document page previews using [generatePreview](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Document#generatePreview(com.groupdocs.annotation.options.pagepreview.PreviewOptions)) method of a [Document](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Document) class.  
[PreviewOptions](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.options.pagepreview/PreviewOptions) class is used to manage preview generation process - specify desired page numbers, image format etc.

Here are the steps to generate document preview with GroupDocs.Annotation API:
*   Create new instance of [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class and pass source document path as a constructor parameter.
*   [Document](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Document) field of [Annotator](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) object allows to access source document and provides [generatePreview](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Document#generatePreview(com.groupdocs.annotation.options.pagepreview.PreviewOptions)) method.
*   Instantiate the [PreviewOptions](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.options.pagepreview/PreviewOptions) object with path format to generated images;
*   Specify image preview format - PNG / JPG / BMP via [setPreviewFormat](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.options.pagepreview/PreviewOptions#setPreviewFormat(int)) method;
*   page numbers to process via setPageNumbers method;
*   Call [generatePreview](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Document#generatePreview(com.groupdocs.annotation.options.pagepreview.PreviewOptions)) method of [Annotator.getDocument()](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator#getDocument()) method result and pass [PreviewOptions](https://apireference.groupdocs.com/java/annotation/com.groupdocs.annotation.options.pagepreview/PreviewOptions) to it.
    
GroupDocs.Annotation provides an ability to choose between image quality and size. **BMP** format should be used for the best image quality. **JPG** format will be useful in case of strict requirements to image size - it produces smallest image size (and faster loading image previews), but with lower quality than **BMP**. By default **PNG** format is selected - which is a golden mean between image quality and size.

The following code snippet demonstrates how to generate document previews.

## Get document page previews 

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-generate-document-pages-preview.java" >}}

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
