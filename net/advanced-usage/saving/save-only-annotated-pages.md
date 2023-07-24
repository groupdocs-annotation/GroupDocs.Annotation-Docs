---
id: save-only-annotated-pages
url: annotation/net/save-only-annotated-pages
title: Save only annotated pages
weight: 2
description: "The page describes how to save only annotated pages when using GroupDocs.Annotation for .NET API."
keywords: annotated pages, save, annotations
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
          text: Call Annotator class .Save() method and pass output path file and in the SaveOptions class set OnlyAnnotationPage to true .
toc: True
---
To export to output document only annotated pages, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [SaveOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) class. Set the [OnlyAnnotatedPages](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions/onlyannotatedpages/) property to `true`.
3.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with the output document path or stream. Specify the [SaveOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) class as a parameter.
The following code snippet shows how to save only annotated pages:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
// for this example input file ("input.pdf") must have at least 10 pages
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
        PageNumber = 9
    };
    //Result file will be contain only two pages (1 and 9)
    annotator.Add(new List<AnnotationBase>() { area, ellipse });
    annotator.Save("result.pdf" new SaveOptions { OnlyAnnotatedPages = true});
}
```
{{< /tab >}}
{{< /tabs >}}
