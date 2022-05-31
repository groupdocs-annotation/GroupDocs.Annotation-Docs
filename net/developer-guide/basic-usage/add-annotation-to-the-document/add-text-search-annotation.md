---
id: add-search-text-annotation
url: annotation/net/add-search-text-annotation
title: Add search text annotation
weight: 13
description: "Learn what is a search text annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a search text annotation, how to add annotation, add search text annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**Search text** annotation adds rectangle with a text inside, like shown at the picture below. 

![](annotation/net/images/add-text-search-annotation.png)
                          

There is an ability to specify the next properties for [SearchTextAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) type:

*   [BackgroundColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/backgroundcolor) - describes area background color;
*   [Text](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/text) - the text you want to find
*   [FontColor](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontcolor) - color of the text
*   [FontFamily](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontfamily) - name of text font;
*   [FontSize](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontsize) - size of text font;

Follow these steps to add [SearchText](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) annotation to document: 

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [SearchText](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [SearchTextAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [SearchTextAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) to the document:

```csharp
//Add search text annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	SearchTextFragment searchText = new SearchTextFragment()
    {
    	Text = "Welcome to GroupDocs",
        FontSize = 10,
        FontFamily = "Calibri",
        FontColor = 65535,
        BackgroundColor = 16761035,
	};
    annotator.Add(searchText);
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
