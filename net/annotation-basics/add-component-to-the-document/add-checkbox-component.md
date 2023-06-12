---
id: add-checkbox-component
url: annotation/net/add-checkbox-component
title: Add checkbox component
weight: 1
description: "The page describes how to add checkbox component to a document using GroupDocs.Annotation for .NET."
keywords: checkbox component, add component
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
        description: Learn how to add check box component to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of CheckBoxComponent class.
        - name: Specify annotation options 
          text: In the CheckBoxComponent class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name CheckBoxComponent.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Checkbox component creates a checkbox like shown in the picture below: 

![](/annotation/net/images/add-checkbox-component.png)

You can specify the following properties of the [CheckBoxComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) class:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/properties/box) defines the annotation position
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/properties/pencolor) defines the frame color

To add a checkbox component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [CheckboxComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [CheckboxComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [CheckboxComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/cropdowncomponent) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	CheckBoxComponent checkbox = new CheckBoxComponent
    {
        Checked = true,
        Box = new Rectangle(100, 100, 100, 100),
        PenColor = 65535,
        Style = BoxStyle.Star,
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
    annotator.Add(checkbox);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}