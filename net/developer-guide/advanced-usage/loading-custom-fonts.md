---
id: loading-custom-fonts
url: annotation/net/loading-custom-fonts
title: Loading custom fonts for documents.
weight: 7
description: "Following this guide you will learn how to load custom fonts for your documents"
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to loading custom fonts
        description: Learn how to loading custom fonts step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass the path to the file with annotations.
        - name: PreviewOptions class declaration
          text: Create an instance of PreviewOptions class.
        - name: Specify ptrview options
          text: In the PreviewOptions class constructor, pass the path to the page.
        - name: Generate preview
          text: Calls the .GeneratePreview() method and pass it the class name PreviewOptions 
toc: True
---

Since 21.5 you are now able to generate preview for documents using custom fonts. In order to realize this opportunity [FontDirectories](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/properties/fontdirectories) option has been added to [LoadOptions](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions) class.

You can now try this feature by using code sample given below:

```csharp
using (Annotator annotator = new Annotator(fs, new LoadOptions { FontDirectories = new List<string> { $"D:/fonts" } }))
{
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"D:/result_{pageNumber}.png";
        return File.Create(pagePath);
    });

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


