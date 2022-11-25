---
id: put-image-annotation-over-text
url: annotation/net/set-document-preview-resolution
title: Set resolution (image quality) of document preview.
weight: 9
description: "Following this guide you will learn how to set resolution(quality) of document preview"
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to set document preview resolution
        description: Learn how to set document preview resolution step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: PreviewOptions class declaration
          text: Create an instance of PreviewOptions class.
        - name: Specify ptrview options
          text: In the PreviewOptions class constructor, pass the path to the page and in its constructor specify the resolution.
        - name: Generate preview
          text: Call the .GeneratePreview() method and pass the class name PreviewOptions to it.
toc: True
---

Since 21.5 you are now able to generate preview for documents with custom resolution. This value is measured on points per inch, default value is 96. In order to use this feature [Resolution](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/resolution) property has been added to [PreviewOptions](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions) class.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result_{pageNumber}.png";
        return File.Create(pagePath);
    })
    {
        Resolution = 144
    };

    annotator.Document.GeneratePreview(previewOptions);
}
```

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
