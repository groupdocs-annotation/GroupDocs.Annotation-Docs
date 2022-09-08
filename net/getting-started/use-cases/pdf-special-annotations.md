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
---

## Special annotations for PDF documents only

We think it's no secret that the PDF format is the most popular format among text documents. Many people prefer to use it because they know that the style and formatting of the document is maintained regardless of the computer or application with which the PDF is viewed. Given its popularity, our .NET API has been improved. We have created annotations unique to the PDF format, the so-called **Components**. As you know, our .NET API supports a large number of annotations that can be applied to different documents - Word documents, Excel sheets, Visio diagrams, PDF etc. But **Component** support PDF only! 


This article will talk about the components that are already implemented in the Annotation .NET API and how you can use them.


### Button component 

**Button component** allows to create button component like shown at the picture below: 

![](/annotation/net/images/add-button-component.png)

There is an ability to specify the next properties for [ButtonComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent) type:

*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/properties/box) - defines annotation position at document page;
*   [PenColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/properties/pencolor) - defines frame color;

Follow these steps to add Button component to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [ButtonComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [ButtonComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [ButtonComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/cropdowncomponent) to the document:

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

### Checkbox component
**Checkbox component** allows to create checkbox component like shown at the picture below: 

![](/annotation/net/images/add-checkbox-component.png)

There is an ability to specify the next properties for [CheckBoxComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) type:

*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/properties/box) - defines annotation position at document page;
*   [PenColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/properties/pencolor) - defines frame color;

Follow these steps to add Checkbox component to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [CheckboxComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [CheckboxComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [CheckboxComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/cropdowncomponent) to the document:

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

### Dropdown component 

**Dropdown component** allows to create combo box with specified options like shown at the picture below: 

![](/annotation/net/images/add-dropdown-component.png)

There is an ability to specify the next properties for [DropdownComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) type:

*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/box) - defines annotation position at document page;
*   [PenColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/pencolor) - defines frame color;
*   [PenStyle](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/penstyle) - defines frame line style (solid, dash, dot etc.);
*   [PenWidth](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/properties/penwidth) - defines frame line width in pixels.

Follow these steps to add Dropdown component to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [DropdownComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [DropdownComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [DropdownComponent](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent) to the document:

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

## Conclusion

In this article we have told you about components that are unique to pdf. We showed you how to add a button, a checkbox and a drop-down list. Now, you should be confident to build your own document annotator using our .NET application API. 

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/net/developer-guide/advanced-usage/_index.md" >}}).
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
