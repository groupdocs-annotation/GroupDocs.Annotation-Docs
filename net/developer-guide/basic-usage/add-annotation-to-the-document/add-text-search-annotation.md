---
id: add-search-text-annotation
url: annotation/net/add-search-text-annotation
title: Add search text annotation
weight: 13
description: "Learn what is a search text annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a search text annotation, how to add annotation, add search text annotation
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
        description: Learn how to add search text fragment annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Annotation class declaration 
          text: Create an instance of SearchTextFragment class.
        - name: Specify annotation options
          text: In the SearchTextFragment class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name SearchTextFragment.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
**Search text** annotation adds rectangle with a text inside, like shown at the picture below. 

![](/annotation/net/images/add-text-search-annotation.png)
                          

There is an ability to specify the next properties for [SearchTextAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) type:

*   [BackgroundColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/backgroundcolor) - describes area background color;
*   [Text](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/text) - the text you want to find
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontcolor) - color of the text
*   [FontFamily](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontfamily) - name of text font;
*   [FontSize](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontsize) - size of text font;

Follow these steps to add [SearchText](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) annotation to document: 

*   Instantiate [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [SearchText](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [SearchTextAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) object;
*   Call [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.

The following code demonstrates how to add [SearchTextAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) to the document:

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
