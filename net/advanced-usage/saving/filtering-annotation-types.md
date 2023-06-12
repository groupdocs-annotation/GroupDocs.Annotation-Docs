---
id: filtering-annotation-types
url: annotation/net/filtering-annotation-types
title: Filtering annotations by type on saving document
weight: 1
description: "This page describes how to filter annotation by type on saving file using GroupDocs.Annotation for .NET API."
keywords: specific annotation types, save annotations
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
toc: True
---
To save only annotations of specific types, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [SaveOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) class. Set the [AnnotationType](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions/properties/annotationtypes) property by specifying annotation type(s) to save.
3.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with the resultant document path or stream. Specify the [SaveOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) class as a parameter.

The following code snippet shows how to save only pages with specific annotation type:

{{< tabs "example1">}}
{{< tab "C#" >}}
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
{{< /tab >}}
{{< /tabs >}}

If you need to save annotations of several types, use the **OR** operator ("|").

The following code snippet shows how to save pages with specific annotation types:

{{< tabs "example2">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	...
    annotator.Save("result.pdf" new SaveOptions { AnnotationTypes = AnnotationType.Ellipse|AnnotationType.Watermark});
}
```
{{< /tab >}}
{{< /tabs >}}