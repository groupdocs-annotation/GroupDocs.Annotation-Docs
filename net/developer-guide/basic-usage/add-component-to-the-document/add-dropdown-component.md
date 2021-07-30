---
id: add-dropdown-component
url: annotation/net/add-dropdown-component
title: Add dropdown component
weight: 1
description: "Learn what is dropdown component and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is dropdown component, how to add component, add dropdown component
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Dropdown component** allows to create combo box with specified options like shown at the picture below: 

![](annotation/net/images/add-dropdown-component.png)

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

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/net/developer-guide/advanced-usage/_index.md" >}}).

### GitHub Examples
You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Annotation for .NET examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
*   [GroupDocs.Annotation for Java examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java)
*   [Document Annotation for .NET MVC UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC)
*   [Document Annotation for .NET App WebForms UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms)
*   [Document Annotation for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Dropwizard)
*   [Document Annotation for Java Spring UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Spring)
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
