---
id: groupdocs-annotation-for-net-21-5-release-notes
url: annotation/net/groupdocs-annotation-for-net-21-5-release-notes
title: GroupDocs.Annotation for .NET 21.5 Release Notes
weight: 80
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---

{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 21.5{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 21.5:
*   Added an ability to load custom fonts for documents
*   Added an ability to specify ZIndex for image annotations for Word formats
*   Added an ability to set up quality of image representation of documents pages	
*   Fixed wrong space appearance in annotations list for html
*   Fixed issues met with TextHighlight/TextUnderline annotations while adding to image
*   Fixed issue during adding watermark annotation on multi-page PDF-file without license

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-1711 | Implement ability to set up image of document quality | Feature |
| ANNOTATIONNET-1689 | Put image annotation top over or add ZIndex property | Feature |
| ANNOTATIONNET-1683 | Add an ability to load custom fonts for documents | Feature |
| ANNOTATIONNET-1688 | NullReferenceException while saving jpeg, jpg file | Bug |
| ANNOTATIONNET-1685 | Wrong space in annotations list for html | Bug |
| ANNOTATIONNET-1675 | Exception during adding watermark annotation on multi-page PDF-file without license | Bug |
| ANNOTATIONNET-1677 | Issues met with TextHighlight/TextUnderline annotations while adding to image | Bug |
| ANNOTATIONNET-1686 | GetDocumentInfo cause exception when open emlx file | Bug |


## Public API and Backward Incompatible Changes

### 1. Loading custom fonts for documents.

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

### 2. Put image annotation top over or add ZIndex property.

Since 21.5 you are now able to specify images placing order for file formats linked to Word. For this purpose a new [ZIndex](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/properties/zindex) property has been added to [ImageAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation) class. You may now try in addition to other properties:

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

### 3. Configure resolution for generated preview images

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