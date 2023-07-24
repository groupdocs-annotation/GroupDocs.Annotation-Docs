---
id: put-image-annotation-over-text
url: annotation/net/set-document-preview-resolution
title: Set resolution of document preview.
weight: 9
description: "The page describes how to set the resolution of document preview"
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

GroupDocs.Annotation v21.5 and later allows you to set resolution of the document's preview. By default, it is 96 points per inch. Set the [Resolution](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/resolution) property of the [PreviewOptions](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions) class to change the resolution.

The following code snippets shows how to set preview resolution to 144 PPI:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"result_{pageNumber}.png";
        return File.Create(pagePath);
    })
    {
        // Set resolution
        Resolution = 144
    };

    annotator.Document.GeneratePreview(previewOptions);
}
```
{{< /tab >}}
{{< /tabs >}}
