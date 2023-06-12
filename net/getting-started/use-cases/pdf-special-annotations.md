---
id: how-to-add-special-annotations-for-pdf
url: annotation/net/how-to-add-special-annotations-for-pdf
title: How to Add Special Annotations for PDF using .NET
weight: 3
description: "Programmatically add special annotations to PDF files. Add button, checkbox, dropdown to PDF using .NET API."
keywords: highlight PDF, pdf button, pdf dropdown, pdf checkbox, pdf component, annotate pdf
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to add special annotations to PDF documents using .NET API.
    showVideo: False
    howTo:
        name: How to add special annotations to PDF
        description: Learn how to add button, checkbox, and dropdown components to the PDF document
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Create component instance
            text: Create an instance of ButtonComponent class and pass parameters.
          - name: Add annotation to the document
            text: Call method Add() on Annotator object and pass ButtonComponent instance there.
          - name: Save document with annotation
            text: Call method Save() on Annotator object and pass output file destination there.
toc: True
---

## Annotations only for PDF documents

PDF is the most popular text document format. It preserves the style and formatting of a document regardless of the computer or application. GroupDocs.Annotation allows you to create annotations that are unique to the PDF format. These annotations are called **Components**.

This article describes the components that are implemented in the GrouDocs.Annotation .NET API.


### Button component 

The **Button** component allows you to create button: 

![](/annotation/net/images/add-button-component.png)

You can specify the following properties of the [ButtonComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent) object:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/properties/box) defines the annotation position at the document page;
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/properties/pencolor) defines the frame color.

To add a **Button** component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object. Specify the input document path or stream.
2.   Instantiate the [ButtonComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent). Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and specify the [ButtonComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent) object.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippets shows how to add the [ButtonComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/cropdowncomponent):

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

### Checkbox component
The **Checkbox** component allows you to create checkbox: 

![](/annotation/net/images/add-checkbox-component.png)

You can specify the following properties of the [CheckBoxComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) object:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/properties/box) defines the annotation position at the document page;
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/properties/pencolor) defines the frame color.

To add the **Checkbox** component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object. Specify the document path or stream.
2.   Instantiate the [CheckboxComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) object. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and specify the [CheckboxComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) object.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [CheckboxComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/cropdowncomponent):

{{< tabs "example2">}}
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

### Dropdown component 

The **Dropdown** component allows you to create combo box: 

![](/annotation/net/images/add-dropdown-component.png)

You can specify the following properties of the [DropdownComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) object:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/box) defines the annotation position at the document page;
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/pencolor) defines the frame color;
*   [PenStyle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/penstyle) defines the frame line style (solid, dash, dot etc.);
*   [PenWidth](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/penwidth) defines the frame line width in pixels.

To add **Dropdown** component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object. Specify the document path or stream.
2.   Instantiate the [DropdownComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) object. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and specify the [DropdownComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) object.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [DropdownComponent](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent):

{{< tabs "example3">}}
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
