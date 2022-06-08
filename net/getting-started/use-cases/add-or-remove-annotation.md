---
id: how-to-add-or-remove-annotation-from-pdf-files
url: annotation/net/how-to-add-or-remove-annotation-from-pdf-files
title: How to Add or Remove Annotations from PDF files using .NET
weight: 1
description: "Programmatically add and remove annotations from PDF files. Add arrow, rectangle annotations and more using .NET API."
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
---

There was a time when we used to discuss document content and feedback in long email threads with multiple attachments and different file versions. Now we can simply use annotations to markup the document with messages and replies and send it. In this article, you will learn how to programmatically annotate PDF documents in .NET with your application. Additionally, we will see how to remove annotations from PDF files using the same .NET API.

### PDF Annotator .NET API

To deal with annotations of your document and images within your .NET applications, GroupDocs provides [GroupDocs.Annotation for .NET](https://products.groupdocs.com/annotation/net). Using the API, you can add, remove, and extract annotations from **word-processing** documents, **spreadsheets**, **presentations**, **images**, **email messages**, Visio **drawings**, some **AutoCAD**, and **digital imaging formats** like **DICOM**. Furthermore, the API allows annotating PDF files. You may have a look at the documentation to know about the long list of [supported document formats for annotation](https://docs.groupdocs.com/annotation/net/supported-document-formats/).

### Download and Configure

[Get the annotation library](https://downloads.groupdocs.com/annotation/net) using NuGet Package Manager in your .NET applications to try the examples of this article. To always stay up to date, make sure you are using latest version of the product. You can find many more example available on [GitHub](https://github.com/groupdocs-annotation). For the details, you may visit the [API Reference](https://apireference.groupdocs.com/annotation/net).

![Nuget Package Manager](annotation/net/images/annotation-nuget.jpg)

Let’s quickly jump to add some of the different kinds of annotations to the PDF document. As there are many different types of annotation, we may not cover all in this article. I will just mention them, and you may [learn about each annotation individually](https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/).

*   Area / Rectangle annotation
*   Arrow
*   Distance
*   Ellipse
*   Highlight
*   Link
*   Point
*   Polyline
*   Replacement
*   Resource Redaction
*   Strikeout
*   Text Field
*   Text Redaction
*   Underline
*   Watermark
    
Let’s start adding some of these in a PDF document.

### Add Arrow Annotation to PDF using .NET

The following are the steps to add arrow annotation to a PDF document.

![Arrow Annotation](annotation/net/images/add-arrow-annotation.png)

*   Load the PDF document using the [Annotator](https://apireference.groupdocs.com/annotation/net/com.groupdocs.annotation/Annotator) class.
*   Initialize arrow annotation using [ArrowAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation) class.
*   Set the position and size of the arrow using [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/arrowannotation/properties/box) property of ArrowAnnotation.
*   Add the created arrow annotation to the Annotator object.
*   Save the annotated PDF by providing the path using the [Save](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save) method.


The following code sample shows how to add arrow annotation to a PDF document using .NET.

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

### Insert Rectangle or Area Annotation to PDF using .NET

You can customize any annotation while adding it to the document. The following are the steps to add rectangle or area annotation to a PDF document with little more customizations. It is similar to adding Arrow annotation but uses **AreaAnnotation** class in place of **ArrowAnnotation**.

*   Load the PDF document using the [Annotator](https://apireference.groupdocs.com/annotation/net/com.groupdocs.annotation/Annotator) class.
*   Initialize rectangle annotation using [AreaAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation) class.
*   Set the position and size of the rectangle using [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/box) property of AreaAnnotation.
*   Set other properties like **PenColor**, **BackgroundColor**, **Opacity**, **PenStyle**, **PenWidth**, and even **Replies**.
*   Add the created rectangle annotation to the Annotator object.
*   Save the annotated PDF by providing the path using the [Save](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save) method.

![Rectangle or Area Annotation](annotation/net/images/add-area-annotation.png)

The following code sample shows how to add rectangle/area annotation to a PDF document using .NET.

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

We have only shown you 2 examples because all the other types of annotation work in a similar way. You can try and add all the other annotations yourself or by following our [detailed guides](https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/) related to every annotation we support.

### Remove Annotations from PDF in .NET

The following steps show how to remove all the annotations from PDF files in .NET.

*   Load the PDF document using the [Annotator](https://apireference.groupdocs.com/annotation/net/com.groupdocs.annotation/Annotator) class.
*   Initialize saving Options using [SaveOptions](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions) class.
*   Set the annotation types to None.
*   Save the PDF file having all the annotations removed, by providing the path using the [save](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save) method.

The following .NET code removes annotations from a PDF file.


```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    SaveOptions options = new SaveOptions();
    options.AnnotationType = AnnotationType.None;
    annotator.Save("result.pdf", options);
}
```

### Conclusion 

In short, you have learned how to add annotations to PDF within .NET applications. Further, you have seen how to remove all the annotations from any PDF file. Now, you should be confident to build your own document annotator .NET application. It can support different types of annotations using GroupDocs.Annotation for .NET.

For more details, options, and examples, you can visit the [documentation](https://docs.groupdocs.com/annotation/net/) and the [GitHub](https://github.com/groupdocs-annotation) repository. For further queries, contact the support on the [forum](https://forum.groupdocs.com/).
