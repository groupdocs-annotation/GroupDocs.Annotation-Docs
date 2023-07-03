---
id: add-search-text-annotation
url: annotation/net/add-search-text-annotation
title: Add search text annotation
weight: 13
description: The page describes how to add search text annotation to a document using GroupDocs.Annotation for .NET."
keywords: search text annotation, add
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
Search text annotation adds a rectangle with a text inside as shown in the picture below:

![](/annotation/net/images/add-text-search-annotation.png)
                          

You can specify the following properties of the [SearchTextAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) class:

*   [BackgroundColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/backgroundcolor) defines the area background color
*   [Text](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/text) defines the text to be found
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontcolor) defines the color of the text
*   [FontFamily](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontfamily) defines the name of text font
*   [FontSize](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/searchtextannotation/properties/fontsize) defines the text font size

To add a search text annotation, follow these steps: 

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [SearchText](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [SearchTextAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows demonstrates how to add [SearchTextAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/searchtextannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
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
{{< /tab >}}
{{< /tabs >}}