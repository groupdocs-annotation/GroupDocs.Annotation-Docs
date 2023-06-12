---
id: add-text-field-annotation
url: annotation/net/add-text-field-annotation
title: Add text field annotation
weight: 13
description: "The page describes how to add text field annotation to a document programmatically using GroupDocs.Annotation for .NET."
keywords: text field annotation, add
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
        description: Learn how to add text field annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Annotation class declaration 
          text: Create an instance of TextFieldAnnotation class.
        - name: Specify annotation options
          text: In the TextFieldAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name TextFieldAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Text field annotation adds a rectangle with a text inside like shown in the picture below:

![](/annotation/net/images/add-text-field-annotation.png)

You can specify the following properties of the [TextFieldAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) class:

*   [BackgroundColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/backgroundcolor) defines the area background color
*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/box) defines the annotation position at the document page
*   [Text](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/text) defines the text to place in the rectangle
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontcolor) defines the color of the text
*   [FontFamily](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontfamily) defines the name of the text font
*   [FontSize](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontsize) defines the size of the text font
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/opacity) allows you to set the annotation opacity
*   [PenStyle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/penstyle) defines the frame line style (solid, dash, dot etc.)
*   [PenWidth](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/penwidth) - defines frame line width in pixels
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/pencolor) defines the frame color
*   [TextHorizontalAlignment]() defines the text horizontal alignment

To add a text field annotation, follow these steps: 

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [TextFieldAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [TextFieldAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.  

The following code snippet shows how to add [TextFieldAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
//Add text field annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	TextFieldAnnotation textField = new TextFieldAnnotation
    {
    	BackgroundColor = 65535,
        Box = new Rectangle(100, 100, 100, 100),
        CreatedOn = DateTime.Now,
        Text = "Some text",
        FontColor = 65535,
        FontSize = 12,
        Message = "This is text field annotation",
        Opacity = 0.7,
        PageNumber = 0,
        PenStyle = PenStyle.Dot,
        PenWidth = 3,
        FontFamily = "Arial",
        TextHorizontalAlignment = HorizontalAlignment.Center,
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
    annotator.Add(textField);
    annotator.Save("result.pdf");
} 
```
{{< /tab >}}
{{< /tabs >}}
