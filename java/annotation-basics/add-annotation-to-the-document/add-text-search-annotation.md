---
id: add-search-text-annotation
url: annotation/java/add-search-text-annotation
title: Add search text annotation
weight: 13
description: The page describes how to add search text annotation to a document using GroupDocs.Annotation for Java."
keywords: search text annotation, add
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
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
          text: Call Annotator class .add() method and pass the class name SearchTextFragment.
        - name: Save document with annotation
          text: Call Annotator class .save() method and pass output path file.
toc: True
---
Search text annotation searches for specific text and highlight it as shown in the picture below:

![](/annotation/net/images/add-text-search-annotation.png)
                          

You can specify the following properties of the [SearchTextAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/) class:

*   [BackgroundColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/#setBackgroundColor-java.lang.Integer-) defines the area background color
*   [Text](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/#setText-java.lang.String-) defines the text to be found. If the document does not contain the specific text, nothing will be highlighted
*   [FontColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/#setFontColor-java.lang.Integer-) defines the color of the text
*   [FontFamily](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/#setFontFamily-java.lang.String-) defines the name of text font
*   [FontSize](hhttps://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/#setFontSize-java.lang.Double-) defines the text font size

To add a search text annotation, follow these steps: 

1.   Instantiate the [Annotator](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/) class. Specify the input document path or stream.
2.   Instantiate the [SearchText](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [SearchTextAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/) class.
4.   Call the [Save](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows demonstrates how to add [SearchTextAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/searchtextfragment/) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
//Add search text annotation to the document from local disk
try(final Annotator annotator = new Annotator("input.pdf")){
	SearchTextFragment searchTextFragment = new SearchTextFragment();
	searchTextFragment.setText("Welcome to GroupDocs");//If the document does not contain this text, nothing will be highlighted
	searchTextFragment.setFontSize(10.);
	searchTextFragment.setFontFamily("Calibri");
	searchTextFragment.setFontColor(65535);
	searchTextFragment.setBackgroundColor(16761035);
	annotator.add(searchTextFragment);
	annotator.save("result_add_search_text.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}