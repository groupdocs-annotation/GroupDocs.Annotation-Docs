---
id: load-document-from-url
url: annotation/java/load-document-from-url
title: Load document from URL
weight: 3
description: "This article explains how to load PDF, Word, Excel, PowerPoint documents from URL when using GroupDocs.Annotation for Java."
keywords: Load document from URL, Load document by URL GroupDocs.Annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: Load document from URL using Java
        description: Load document from URL for annotate pdfs, words and other documents natively on mac, windows or ubuntu with high performance using Java language and GroupDocs.Annotation for Java APIs
        productCode: annotation
        productPlatform: java 
    showVideo: True
    howTo:
        name: How to load document from URL with in Java
        description: Learn how to load document with mark up words, pdf or other document in Java step by step
        steps:
        - name: Load pdf, word or other document file
          text: Create an instance of Annotator class and pass source document file path as a constructor parameter.
        - name: Set data for arrow annotation
          text: Create an instance of ArrowAnnotation class (for example) and add data for arrow annotation.
        - name: Add annotation to document and save result
          text: Call Annotator class Add method and pass the ArrowAnnotation object from the previous step as parameter then call Save method from Annotator class and pass the output filename as parameter.
toc: True
---

Following example demonstrates how to annotate document from URL.

{{< gist "groupdocs-annotation-gists" "6417f1b3b8fc9edeeb070f2cfad3edcc" "java-load-document-from-url.java" >}}

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
