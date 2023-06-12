---
id: add-image-annotation
url: annotation/net/add-image-annotation
title: Add image annotation
weight: 6
description: "The page describes how to add image annotation to a document using GroupDocs.Annotation for .NET."
keywords: image, add, annotation
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
        description: Learn how to add image annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration          
          text: Create an instance of ImageAnnotation class.
        - name: Specify annotation options 
          text: In the ImageAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ImageAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Image annotation allows you to add an image on document page like shown in the picture below:

![](/annotation/net/images/add-image-annotation.png)

You can set the following properties of the [ImageAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/imageannotation) class:

*   [ImagePath](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/imagepath) defines the image local or remote path
*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/box) defines the annotation position on the page using the [Rectangle](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models/rectangle) structure (image will be resized for specified width and height)
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/opacity) allows you to set the annotation opacity (present in all supported formats, examples of it you can see above)
*   [Angle]() defines the annotation rotation angle

To add an image annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [ImageAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method. Specify the [ImageAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/imageannotation) class.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add [ImageAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/imageannotation) to the document:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
            {
                ImageAnnotation area = new ImageAnnotation
                {
                    Box = new Rectangle(100, 100, 100, 100),
                    Opacity = 0.7,
                    PageNumber = 0,
                    ImagePath = "www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png",
                    Angle = 100
                };
                annotator.Add(area);
                annotator.Save("result.pdf");
            }
```
{{< /tab >}}
{{< /tabs >}}