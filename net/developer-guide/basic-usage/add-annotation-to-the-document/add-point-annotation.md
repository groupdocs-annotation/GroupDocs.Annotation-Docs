---
id: add-point-annotation
url: annotation/net/add-point-annotation
title: Add point annotation
weight: 8
description: "Learn what is a point annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a point annotation, how to add annotation, add point annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Point** annotation sticks comments to any point in a document like shown at the picture below. 

![](annotation/net/images/add-point-annotation.png)

There is an ability to specify the next properties for [PointAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/pointannotation) type:

*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/pointannotation/properties/box) – defines annotation position at document page;  
    

Follow these steps to add Point annotation to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [PointAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/pointannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [PointAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/pointannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream. 

The following code demonstrates how to add [PointAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/pointannotation) to the document:

```csharp
//Add point annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	PointAnnotation point = new PointAnnotation
    {
    	Box = new Rectangle(100, 100, 0, 0),
        CreatedOn = DateTime.Now,
        Message = "This is point annotation",
        PageNumber = 0,
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
    annotator.Add(point);
    annotator.Save("result.pdf"));
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