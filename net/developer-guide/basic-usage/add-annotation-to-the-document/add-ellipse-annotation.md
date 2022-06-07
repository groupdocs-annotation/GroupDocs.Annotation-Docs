---
id: add-ellipse-annotation
url: annotation/net/add-ellipse-annotation
title: Add ellipse annotation
weight: 4
description: "Learn what is an ellipse annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a ellipse annotation, how to add annotation, add ellipse annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Ellipse annotation** draws elliptic annotation in a document page like shown at the picture below.

![](annotation/net/images/add-ellipse-annotation.png)

There is an ability to specify the next properties for [EllipseAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/ellipseannotation) type: 

*   [BackgroundColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/backgroundcolor) - describes ellipse background color;
*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/box) - defines annotation position at document page;
*   [Opacity](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) - allows to set annotation opacity;
*   [PenColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/pencolor) - defines pen color;
*   [PenStyle](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/penstyle) - defines line style (solid, dash, dot etc.);
*   [PenWidth](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/penwidth) - defines line width in pixels. 

Follow these steps to add Ellipse annotation to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [EllipseAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/ellipseannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [EllipseAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/ellipseannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [EllipseAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/ellipseannotation) to the document:

```csharp
//Add ellipse annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	EllipseAnnotation ellipse = new EllipseAnnotation
    {
    	BackgroundColor = 65535,
        Box = new Rectangle(100, 100, 100, 100),
        CreatedOn = DateTime.Now,
        Message = "This is ellipse annotation",
        Opacity = 0.7,
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
   annotator.Add(ellipse);
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
