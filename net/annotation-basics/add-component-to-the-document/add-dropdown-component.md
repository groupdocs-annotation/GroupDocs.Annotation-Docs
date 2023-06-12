---
id: add-dropdown-component
url: annotation/net/add-dropdown-component
title: Add dropdown component
weight: 1
description: "The page describes how to add dropdown component to a document using GroupDocs.Annotation for .NET."
keywords: dropdown component, add component
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
        description: Learn how to add drop down component to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of DropdownComponent class.
        - name: Specify annotation options 
          text: In the DropdownComponent class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name DropdownComponent.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Dropdown component creates a combo box like shown in the picture below: 

![](/annotation/net/images/add-dropdown-component.png)

You can specify the following properties of the [DropdownComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) class:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/box) defines the annotation position
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/pencolor) defines the frame color
*   [PenStyle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/penstyle) defines the frame line style (solid, dash, dot etc.)
*   [PenWidth](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/penwidth) defines the frame line width in pixels.

To add a dropdown component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [DropdownComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [DropdownComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [DropdownComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	DropdownComponent dropdown = new DropdownComponent
    {
        Options = new List<string> { "Item1", "Item2", "Item3" },
        SelectedOption = null,
        Placeholder = "Choose option",
        Box = new Rectangle(100, 100, 100, 100),
        CreatedOn = DateTime.Now,
        Message = "This is dropdown component",
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
    annotator.Add(dropdown);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}