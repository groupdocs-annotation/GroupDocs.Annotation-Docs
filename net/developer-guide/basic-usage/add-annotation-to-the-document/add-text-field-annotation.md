---
id: add-text-field-annotation
url: annotation/net/add-text-field-annotation
title: Add text field annotation
weight: 13
description: "Learn what is a text field annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a text field annotation, how to add annotation, add text field annotation
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
**Text field** annotation adds rectangle with a text inside, like shown at the picture below. 

![](/annotation/net/images/add-text-field-annotation.png)

There is an ability to specify the next properties for [TextFieldAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) type:

*   [BackgroundColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/backgroundcolor) - describes area background color;
*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/box) - defines annotation position at document page;
*   [Text](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/text) - text that will be appear in rectangle
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontcolor) - color of the text
*   [FontFamily](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontfamily) - name of text font;
*   [FontSize](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontsize) - size of text font;
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/opacity) - allows to set annotation opacity;
*   [PenStyle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/penstyle) - defines frame line style (solid, dash, dot etc.);
*   [PenWidth](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/penwidth) - defines frame line width in pixels;
*   [PenColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/pencolor) - defines frame color;
*   [TextHorizontalAlignment]() - defines text horizontal alignment.

Follow these steps to add [TextField](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) annotation to document: 

*   Instantiate [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [TextFieldAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [TextFieldAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) object;
*   Call [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [TextFieldAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) to the document:

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
