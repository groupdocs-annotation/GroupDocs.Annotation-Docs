---
id: comparing-annotations-using-equals-method
url: annotation/java/comparing-annotations-using-equals-method
title: Comparing annotations using the equals method
weight: 6
description: "Following this guide you will learn how to compare annotations using equals method of document using GroupDocs.Annotation for Java API."
keywords: Equals, Compare, Annotation, Annotations, Comparing, Compare annotations
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: Comparing annotations in document using Java
        description: Comparing annotation of pdf, word, images and other documents using Java language and GroupDocs.Annotation for Java APIs
        productCode: annotation
        productPlatform: java 
    showVideo: True
---
Since from 21.7.
You have the ability to compare annotations using the [Equals]() method.

Here is the example of the code:

```java
try (Annotator annotator = new Annotator("annotated_file.pdf")) {
    List<AnnotationBase> annotations = annotator.get();
    ImageAnnotation imageAnnotation = new ImageAnnotation();
    imageAnnotation.setBox(new Rectangle(100, 100, 100, 100));
    imageAnnotation.setOpacity(0.7);
    imageAnnotation.setPageNumber(0);
    imageAnnotation.setImagePath("www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png");
    imageAnnotation.setAngle(100.0);

    for(int i = 0; i < annotations.size(); i++) {
        if (imageAnnotation.equals(annotations.get(i))) {
                // Do some stuff here...
        }
    }
}
```

## More resources
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
