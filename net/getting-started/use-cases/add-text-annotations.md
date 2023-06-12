---
id: how-to-add-text-annotations-to-pdf-file
url: annotation/net/how-to-add-text-annotations-to-pdf-file
title: How to Add Text Annotations to PDF files using .NET
weight: 2
description: "How to add the text annotations to PDF files. Add text field and strikeout annotations using .NET API."
keywords: highlight PDF, add annotations in PDF, annotate PDF, strikeout text for PDF
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to add text annotations to PDF documents using .NET API.
    showVideo: False
    howTo:
        name: How to add text annotations
        description: Learn how to add text field and strikeout annotations to the PDF document
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Annotation class declaration
            text: Create an instance of TextFieldAnnotation or StrikeoutAnnotation class.
          - name: Specify annotation options 
            text: In the TextFieldAnnotation or StrikeoutAnnotation class constructor pass parameters.
          - name: Add annotation to the document
            text: Call method Add() on Annotator object and pass TextFieldAnnotation or StrikeoutAnnotation instance there.
          - name: Save document with annotation
            text: Call method Save() on Annotator object and pass output file destination there.
toc: True
---


## Text annotations

GroupDocs.Annotation allows you to add different text annotations to a PDF document, such as: 

* [Highlight annotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation)
* [Link annotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation)
* [Replacement annotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation)
* [Strikeout annotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/strikeoutannotation)
* [Text field annotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation)
* [Text redaction annotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textredactionannotation)
* [Squiggly annotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation)
* [Underline annotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/underlineannotation)

This article describes how to add the highlight and strikeout annotations to a PDF document. You can add other annotations in the same way.

### Highlight Annotation 

The highlight annotation highlights and comments selected text:

![](/annotation/net/images/add-highlight-annotation.png)

You can specify the following properties of the [HighlightAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) type:

*   [BackgroundColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/backgroundcolor) specifies the annotation background color;
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation/properties/fontcolor) specifies the color of annotation text;
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) allows you to set annotation opacity;
*   [Points](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation/properties/points) specifies the annotation positions as array of points.

To add a highlight annotation to document, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class with input document path or stream;
2.   Instantiate the [HighlightAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) class with appropriate properties (position, page number, etc);
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and specify the [HighlightAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) object;
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method.  
      

The following code snippet shows how to add a highlight annotation to a document:

{{< tabs "example1">}}
{{< tab "C#" >}} 
```csharp
// Add highlight annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	HighlightAnnotation highlight = new HighlightAnnotation
    {
    	BackgroundColor = 65535,
        CreatedOn = DateTime.Now,
        FontColor = 0,
        Message = "This is highlight annotation",
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
        	new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
        },
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
    annotator.Add(highlight);
    annotator.Save("result.pdf");
} 
```
{{< /tab >}}
{{< /tabs >}}

### Strikeout Annotation

Strikeout annotation marks text fragment with a strike-through styling:

![](/annotation/net/images/add-strikeout-annotation.png)

The GroupDocs.Annotation allows you to specify the following properties of the [StrikeoutAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/strikeoutannotation) type:

1.   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/strikeoutannotation/properties/fontcolor) specifies the color of annotation text;
2.   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) allows you to set annotation opacity;
3.   [Points](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/strikeoutannotation/properties/points) specifies the annotation positions as array of points.  
      


To add a strikeout annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class with input document path or stream;
2.   Instantiate the [StrikeoutAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/strikeoutannotation) class with appropriate properties (position, page number, etc);
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and specify the [StrikeoutAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/strikeoutannotation) object;
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method.
 


The following code snippet shows how to add a strikeout annotation to the document:

{{< tabs "example2">}}
{{< tab "C#" >}} 
```csharp
//Add strikeout annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	StrikeoutAnnotation strikeout = new StrikeoutAnnotation
    {
    	CreatedOn = DateTime.Now,
        FontColor = 65535,
        BackgroundColor = 16761035,
        Message = "This is strikeout annotation",
        Opacity = 0.7,
        PageNumber = 0,
        Points = new List<Point>
        {
        	new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
        },
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
     annotator.Add(strikeout);
     annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}
