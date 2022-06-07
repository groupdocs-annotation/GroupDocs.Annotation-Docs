---
id: add-highlight-annotation
url: annotation/net/add-highlight-annotation
title: Add highlight annotation
weight: 5
description: "Learn what is a highlight annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a highlight annotation, how to add annotation, add highlight annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Highlight** annotation highlights and comments selected text  like shown at the picture below. 

![](annotation/net/images/add-highlight-annotation.png)

There is an ability to specify the next properties for [HighlightAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) type:

*   [BackgroundColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/backgroundcolor) - describes annotation background color;
*   [FontColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation/properties/fontcolor) - color of annotation text;
*   [Opacity](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/areaannotation/properties/opacity) - allows to set annotation opacity;
*   [Points](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/linkannotation/properties/points) - annotation positions set by array of points.

Follow these steps to add Highlight annotation to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [HighlightAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [HighlightAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.  
      
    

The following code demonstrates how to add [HighlightAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/highlightannotation) to the document:

```csharp
//Add highlight annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	HighlightAnnotation highlight = new HighlightAnnotation
    {
    	BackgroundColor = 65535,
        CreatedOn = DateTime.Now,
        FontColor = 0,
        Message = "This is highlight annotation",
        Opacity = 0.5,
        PageNumber = 0,
        Points = new List<Point>
        {
        	new Point(80, 730), new Point(240, 730), new Point(80, 650), new Point(240, 650)
        },
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
    annotator.Add(highlight);
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