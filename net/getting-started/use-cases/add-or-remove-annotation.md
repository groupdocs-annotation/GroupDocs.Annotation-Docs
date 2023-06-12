---
id: how-to-add-or-remove-annotation-from-pdf-files
url: annotation/net/how-to-add-or-remove-annotation-from-pdf-files
title: How to Add or Remove Annotations in PDF files using .NET
weight: 1
description: "Add and remove annotations from PDF files. Add arrow, rectangle annotations and more using .NET API."
keywords: highlight PDF, add annotations in PDF, Annotate PDF, Remove annotations from PDF, 
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to add and remove annotations from PDF documents. Add arrow, rectangle annotations and more using .NET API.
    showVideo: False
    howTo:
        name: How to add and remove annotations
        description: Learn how to add arrow and rectangle annotations to the PDF document
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Annotation class declaration
            text: Create an instance of ArrowAnnotation or AreaAnnotation class.
          - name: Specify annotation options 
            text: In the ArrowAnnotation or AreaAnnotation class constructor pass parameters.
          - name: Add annotation to the document
            text: Call method Add() on Annotator object and pass ArrowAnnotation or AreaAnnotation instance there.
          - name: Save document with annotation
            text: Call method Save() on Annotator object and pass output file destination there.
toc: True
---

This article describes how to annotate PDF documents and remove annotations within your .NET application.

### Add Arrow Annotation to a PDF File

To add arrow annotation to a PDF document, follow these steps:

![Arrow Annotation](/annotation/net/images/add-arrow-annotation.png)

1.   Load the PDF file using the [Annotator](https://reference.groupdocs.com/annotation/net/com.groupdocs.annotation/Annotator) class.
2.   Initialize arrow annotation using the [ArrowAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation) class.
3.   Set the position and size of the arrow using the [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation/properties/box) property of the [ArrowAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation) class.
4.   Add the created arrow annotation to the Annotator object.
5.   Save the annotated PDF using the [Save](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save) method.


The following code snippet shows how to add arrow annotation to a PDF file:

{{< tabs "example1">}}
{{< tab "C#" >}} 
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	ArrowAnnotation arrow = new ArrowAnnotation
    {
        Box = new Rectangle(100, 100, 100, 100),
        CreatedOn = DateTime.Now,
        Message = "This is arrow annotation",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = 65535,
        PenStyle = PenStyle.Dot,
        PenWidth = 3,
        Replies = new List<Reply>
        {
        	new Reply
            {
            	Comment = "First comment",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
             	Comment = "Second comment",
                RepliedOn = DateTime.Now
            }
        }
    };
    annotator.Add(arrow);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}   

### Add a Rectangle or Area Annotation to PDF file

To add a rectangle or area annotation to a PDF file, use the `AreaAnnotation` class instead of the `ArrowAnnotation`. Follow these steps:

1.   Load a PDF document using the [Annotator](https://reference.groupdocs.com/annotation/net/com.groupdocs.annotation/Annotator) class.
2.   Initialize a rectangle annotation using the [AreaAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation) class.
3.   Set the size and position of the rectangle using the [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/box) property of the [AreaAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation).
4.   If needed, specify the other properties such as **PenColor**, **BackgroundColor**, **Opacity**, **PenStyle**, **PenWidth**, and **Replies**.
5.   Add the created rectangle annotation to the `Annotator` object.
6.   Save the annotated PDF using the [Save](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save) method.

![Rectangle or Area Annotation](/annotation/net/images/add-area-annotation.png)

The following code snippet shows how to add rectangle/area annotation to a PDF file:

{{< tabs "example2">}}
{{< tab "C#" >}} 
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	AreaAnnotation area = new AreaAnnotation
    {
     	BackgroundColor = 65535,
        Box = new Rectangle(100, 100, 100, 100),
        CreatedOn = DateTime.Now,
        Message = "This is area annotation",
        Opacity = 0.7,
        PageNumber = 0,
        PenColor = 65535,
        PenStyle = PenStyle.Dot,
        PenWidth = 3,
        Replies = new List<Reply>
        {
        	new Reply
            {
            	Comment = "First comment",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
            	Comment = "Second comment",
                RepliedOn = DateTime.Now
            }
        }
    };
    annotator.Add(area);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}  

You can add annotations of other types in a similar way. You can try and add all the other annotations as described in [detailed guides](https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/) related to every annotation we support.

### Remove Annotations from PDF in .NET

To remove all the annotations from PDF files, follow these steps

1.   Load the PDF document using the [Annotator](https://reference.groupdocs.com/annotation/net/com.groupdocs.annotation/Annotator) class.
2.   Initialize saving options using the [SaveOptions](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions) class.
3.   Set the annotation types to `None`.
4.   Save the PDF file using the [Save](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save) method.

The following .NET code removes annotations from a PDF file.

{{< tabs "example3">}}
{{< tab "C#" >}} 
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    SaveOptions options = new SaveOptions();
    options.AnnotationType = AnnotationType.None;
    annotator.Save("result.pdf", options);
}
```
{{< /tab >}}
{{< /tabs >}}

