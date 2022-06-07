---
id: add-image-annotation
url: annotation/net/add-image-annotation
title: Add image annotation
weight: 6
description: "Learn what is a image annotation and how to add it to a document programmatically using GroupDocs.Annotation for .NET."
keywords: What is a image annotation, how to add annotation, add image annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
**[Image annotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/imageannotation)** allows to add image within document page like shown at the picture below.

![](annotation/net/images/add-image-annotation.png)

There is an ability to specify the next properties for [ImageAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/imageannotation) type:

*   [ImagePath](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/imagepath) – defines image local or remote path.
*   [Box](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/box) – defines annotation position at document page using [Rectangle](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models/rectangle) structure;
    (image will be resized for your custom width and height)
*   [Opacity](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/opacity) – allows to set annotation opacity (present in all supported formats, examples of it you can see above);
*   [Angle]() – defines annotation rotation angle.

Follow these steps to add Highlight annotation to document:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [ImageAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation) object with desired properties (position, page number, etc);
*   Call [Add](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass ImageAnnotation object;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save) method with resultant document path or stream.  

The following code demonstrates how to add [ImageAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/imageannotation) to the document:

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