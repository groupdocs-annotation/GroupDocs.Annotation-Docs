---
id: load-document-from-stream
url: annotation/net/load-document-from-stream
title: Load document from stream
weight: 2
description: "This article explains how to load PDF, Word, Excel, PowerPoint documents from stream when using GroupDocs.Annotation for .NET."
keywords: Load document from stream, Load document with GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to load document from stream
        description: Learn how to load document from stream step by step
        steps:
        - name: Document stream
          text: Load source file an instance documentStream with definition OpenRead
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass document stream to it. You may specify absolute or relative file path as per your requirements.
        - name: Annotation class declaration
          text: Create an instance of annotation class.
        - name: Specify annotation options 
          text: In the annotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name annotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file with class SaveOptions.
---
There might be the case when source or target document is not physically located on the disk. Instead, you have the document in the form of a stream. In this case, to avoid the overhead of saving stream as a file on disk, [**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) provides a way to work with document streams directly.   
  
The following are the steps to be followed:

*   Obtain document stream; 
*   Pass opened source document stream to [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class constructor.

Following code snippet describes this case.

```csharp
using (documentStream = File.OpenRead("input.pdf"))
using (Annotator annotator = new Annotator(documentStream))
{
     	AreaAnnotation area = new AreaAnnotation()
       {
       	Box = new Rectangle(100, 100, 100, 100),
       	BackgroundColor = 65535,
       };
       annotator.Add(area);
       annotator.Save("result.pdf", new SaveOptions());
}

```

## More resources

### GitHub Examples
You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Annotation for .NET examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
*   [GroupDocs.Annotation for Java examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java)
*   [Document Annotation for .NET MVC UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC)
*   [Document Annotation for .NET App WebForms UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms)
*   [Document Annotation for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Dropwizard)
*   [Document Annotation for Java Spring UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Spring)
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
