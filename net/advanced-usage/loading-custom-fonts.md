---
id: loading-custom-fonts
url: annotation/net/loading-custom-fonts
title: Load custom fonts.
weight: 7
description: "The page describes how to load custom fonts."
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

GroupDocs.Annotation v21.5 and later allows you to generate preview for documents using custom fonts. To do this, specify the [FontDirectories](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/properties/fontdirectories) property of the [LoadOptions](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions) class.

The following code snippet shows how to use custom fonts while generating preview:

{{< tabs "example1">}}
{{< tab "C#" >}}
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
{{< /tab >}}
{{< /tabs >}}