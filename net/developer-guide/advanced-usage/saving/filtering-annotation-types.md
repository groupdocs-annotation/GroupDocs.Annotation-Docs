---
id: filtering-annotation-types
url: annotation/net/filtering-annotation-types
title: Filtering annotation types on document save
weight: 1
description: "Learn this guide to check how to filter annotation types during saving document using GroupDocs.Annotation for .NET API."
keywords: save specific annotation types, save annotations
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to annotate a document
        description: Learn how to add area annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of AreaAnnotation class and EllipseAnnotation class.
        - name: Specify annotation options 
          text: In the AreaAnnotation class and EllipseAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: In the .Add() method, create a new instance of the annotation collections and pass the annotation names to it.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file and class SaveOptions with the annotation type you want to save.
---
This feature can be using when need to save only specific annotation types and ignore others.

The following are the steps how to filter exported annotations to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [SaveOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) object and set [AnnotationType](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions/properties/annotationtypes) desired annotation type(s), that will presented in resultant document;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream and [SaveOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) object;

Following code snippet shows how to save only pages with specific annotation type

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	AreaAnnotation area = new AreaAnnotation()
    {
    	Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 65535,
        PageNumber = 1
    };
    EllipseAnnotation ellipse = new EllipseAnnotation()
    {
        Box = new Rectangle(100, 100, 100, 100),
        BackgroundColor = 123456,
        PageNumber = 1
    };
    annotator.Add(new List<AnnotationBase>() { area, ellipse });
	
	//Result file will contains only ellipse annotations.
    annotator.Save("result.pdf" new SaveOptions { AnnotationTypes = AnnotationType.Ellipse});
}
```

If you need to add more than one annotation filter, you can using logical operator "OR" ("|"):

Following code snippet shows how to save pages with specific multiple annotation types

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	...
    annotator.Save("result.pdf" new SaveOptions { AnnotationTypes = AnnotationType.Ellipse|AnnotationType.Watermark});
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
