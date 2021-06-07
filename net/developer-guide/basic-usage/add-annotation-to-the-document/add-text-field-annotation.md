---
id: add-text-field-annotation
url: annotation/net/add-text-field-annotation
title: Add text field annotation
weight: 13
description: "Learn what is a text field annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a text field annotation, how to add annotation, add text field annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Text field** annotation adds rectangle with a text inside, like shown at the picture below. 

![](annotation/net/images/add-text-field-annotation.png)

There is an ability to specify the next properties for [TextFieldAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) type:

*   [BackgroundColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/backgroundcolor) - describes area background color;
*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/box) - defines annotation position at document page;
*   [Text](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/text) - text that will be appear in rectangle
*   [FontColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontcolor) - color of the text
*   [FontFamily](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontfamily) - name of text font;
*   [FontSize](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/fontsize) - size of text font;
*   [Opacity](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/opacity) - allows to set annotation opacity;
*   [PenStyle](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/penstyle) - defines frame line style (solid, dash, dot etc.);
*   [PenWidth](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/penwidth) - defines frame line width in pixels;
*   [PenColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textfieldannotation/properties/pencolor) - defines frame color;
*   [TextHorizontalAlignment]() - defines text horizontal alignment.

Follow these steps to add [TextField](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) annotation to document: 

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [TextFieldAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [TextFieldAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [TextFieldAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textfieldannotation) to the document:

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
