---
id: add-text-redaction-annotation
url: annotation/net/add-text-redaction-annotation
title: Add text redaction annotation
weight: 14
description: "Learn what is a text redaction annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a text redaction annotation, how to add annotation, add text redaction annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Text redaction** annotation fills part of text with black rectangle (used if you want to hide some text) like shown at the picture below.

![](annotation/net/images/add-text-redaction-annotation.png)

There is an ability to specify the next properties for [TextRedactionAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textredactionannotation) type

*   [Points](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/textredactionannotation/properties/points) - annotation positions set by array of points.  
    

Follow these steps to add text redaction annotation to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [TextRedactionAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textredactionannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [TextRedactionAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textredactionannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.  

The following code demonstrates how to add [TextRedactionAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/textredactionannotation) to the document:

```csharp
//Add text redaction annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	TextRedactionAnnotation textRedaction = new TextRedactionAnnotation
    {
    	CreatedOn = DateTime.Now,
        Message = "This is text redaction annotation",
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
     annotator.Add(textRedaction);
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
