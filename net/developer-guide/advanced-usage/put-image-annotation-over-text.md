---
id: put-image-annotation-over-text
url: annotation/net/put-image-annotation-over-text
title: Put image annotations over the text (setting up ZIndex of image).
weight: 8
description: "Following this guide you will learn how set ZIndex of image to put it over the other text"
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
Since 21.5 you are now able to specify images placing order for file formats linked to Word. For this purpose a new [ZIndex](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/zindex) property has been added to [ImageAnnotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation) class. You may now try in addition to other properties:

```csharp
ImageAnnotation area = new ImageAnnotation
{
    Box = new Rectangle(100, 100, 100, 100),
    Opacity = 0.7,
    PageNumber = 0,
    ImagePath = "www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png",
    Angle = 100,
    ZIndex = 3
};
```

{{< alert style="info" >}}Supported only for Words documents, other formats ignore this property{{< /alert >}}

## More resources
### GitHub Examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Annotation for .NET examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
*   [GroupDocs.Annotation for Java examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java)
*   [Document Annotation for .NET MVC UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC)
*   [Document Annotation for .NET App WebForms UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms)
*   [Document Annotation for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Dropwizard)
*   [Document Annotation for Java Spring UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Spring)
### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.

