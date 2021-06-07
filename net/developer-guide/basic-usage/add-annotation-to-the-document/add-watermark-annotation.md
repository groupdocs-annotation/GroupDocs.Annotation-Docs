---
id: add-watermark-annotation
url: annotation/net/add-watermark-annotation
title: Add watermark annotation
weight: 16
description: "Learn what is a watermark annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a watermark annotation, how to add annotation, add watermark annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Watermark** annotation adds text watermark like shown at the picture below. 

![](annotation/net/images/add-watermark-annotation.png)

There is an ability to specify the next properties for [WatermarkAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) type:

*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/box) - defines annotation position at document page;
*   [Text](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/text) - text of watermark;
*   [FontColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontcolor) - color of annotation text;
*   [FontFamily](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontfamily) - font of annotation text;
*   [FontSize](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontsize) - size of text font;
*   [Opacity](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/opacity) - allows to set annotation opacity;
*   [Angle](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/angle) - watermark text angle;
*   [VerticalAlignment]() - defines vertical alignment on document;
*   [HorizontalAlignment]() - defines horizontal alignment on document.

Follow these steps to add Watermark annotation to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [WatermarkAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) object with desired properties (position, color, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [WatermarkAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

  

The following code demonstrates how to add [WatermarkAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) to the document:

```csharp
//Add watermark annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	WatermarkAnnotation watermark = new WatermarkAnnotation
    {
    	Angle = 75,
        Box = new Rectangle(200, 200, 100, 50),
        CreatedOn = DateTime.Now,
        Text = "Watermark",
        FontColor = 65535,
        FontSize = 12,
        Message = "This is watermark annotation",
        Opacity = 0.7,
        HorizontalAlignment = HorizontalAlignment.Center,
        VerticalAlignment = VerticalAlignment.Center,
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
    annotator.Add(watermark);
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