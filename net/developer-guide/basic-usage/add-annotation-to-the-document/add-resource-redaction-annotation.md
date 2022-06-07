---
id: add-resource-redaction-annotation
url: annotation/net/add-resource-redaction-annotation
title: Add resource redaction annotation
weight: 11
description: "Learn what is a resource redaction annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a resource redaction annotation, how to add annotation, add resource redaction annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Resource redaction** annotation fills black rectangle with fixed position (used if you want to hide some text) like shown at the picture below. 

![](annotation/net/images/add-resource-redaction-annotation.png)

There is an ability to specify the next properties for [ResourcesRedactionAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) type:

*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation/properties/box) – defines annotation position at document page;  
      
    

Follow these steps to add Resource redaction annotation to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [ResourceRedactionAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [ResourceRedactionAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [ResourcesRedactionAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/resourcesredactionannotation) to the document:

```csharp
//Add resource redaction annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	ResourcesRedactionAnnotation resourcesRedaction = new ResourcesRedactionAnnotation
    {
    	Box = new Rectangle(100, 100, 100, 100),
        CreatedOn = DateTime.Now,
        Message = "This is resources redaction annotation",
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
   annotator.Add(resourcesRedaction);
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