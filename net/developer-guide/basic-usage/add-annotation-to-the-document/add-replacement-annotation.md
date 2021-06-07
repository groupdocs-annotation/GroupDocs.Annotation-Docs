---
id: add-replacement-annotation
url: annotation/net/add-replacement-annotation
title: Add replacement annotation
weight: 10
description: "Learn what is a replacement annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a replacement annotation, how to add annotation, add replacement annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Replacement** annotation replaces original text with other provided text fragment. Please check the picture below to know how replacement annotation may look like. 

![](annotation/net/images/add-replacement-annotation.png)

There is an ability to specify the next properties for [ReplacementAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/replacementannotation) type:

*   [FontColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation/properties/fontcolor) - color of annotation text;
*   [Opacity](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation/properties/opacity) \- allows to set annotation opacity;
*   [Points](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation/properties/points) - annotation positions set by array of points;
*   [TextToReplace](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/replacementannotation/properties/texttoreplace) - text that will be replaced   
     

Follow these steps to add Replacement annotation to document: 

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [ReplacementAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/replacementannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [ReplacementAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/replacementannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream;

  

The following code demonstrates how to add [ReplacementAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/replacementannotation) to the document:

```csharp
//Add replacement annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	ReplacementAnnotation replacement = new ReplacementAnnotation
    {
    	CreatedOn = DateTime.Now,
        FontColor = 65535,
        Message = "This is replacement annotation",
        Opacity = 0.7,
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
         },
         TextToReplace = "replaced text"
     };
     annotator.Add(replacement);
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