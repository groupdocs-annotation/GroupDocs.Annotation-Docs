---
id: add-button-component
url: annotation/net/add-button-component
title: Add button component
weight: 1
description: "The page describes how to add button component to a document using GroupDocs.Annotation for .NET."
keywords: button component, add
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
        description: Learn how to add button component to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of ButtonComponent class.
        - name: Specify annotation options 
          text: In the ButtonComponent class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ButtonComponent.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Button component creates a button component like shown in the picture below: 

![](/annotation/net/images/add-button-component.png)

You can specify the following properties of the [ButtonComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent) class:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/properties/box) defines the annotation position
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/properties/pencolor) defines the frame color

To add a button component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [ButtonComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [ButtonComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [ButtonComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/cropdowncomponent) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	ButtonComponent button = new ButtonComponent
    {
        CreatedOn = DateTime.Now,
        Style = BorderStyle.Dashed,
        Message = "This is button component",
        BorderColor = 1422623,
        PenColor = 14527697,
        ButtonColor = 10832612,
        PageNumber = 0,
        BorderWidth = 12,
        Box = new Rectangle(100, 300, 90, 30),
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
    annotator.Add(button);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}