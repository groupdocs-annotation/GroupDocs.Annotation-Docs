---
id: add-checkbox-component
url: annotation/net/add-checkbox-component
title: Add checkbox component
weight: 1
description: "Learn what is checkbox component and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is checkbox component, how to add component, add checkbox component
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
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          text: Create an instance of CheckBoxComponent class.
          text: In the CheckBoxComponent class constructor, pass parameters.
          text: Call Annotator class .Add() method and pass the class name CheckBoxComponent.
          text: Call Annotator class .Save() method and pass output path file.
---
**Checkbox component** allows to create checkbox component like shown at the picture below: 

![](annotation/net/images/add-checkbox-component.png)

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
