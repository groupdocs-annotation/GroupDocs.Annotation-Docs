---
id: groupdocs-annotation-for-net-21-3-release-notes
url: annotation/net/groupdocs-annotation-for-net-21-3-release-notes
title: GroupDocs.Annotation for .NET 21.3 Release Notes
weight: 100
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 21.3{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 21.3:
*   Implemented getting information about text coordinates in the documents for all supported formats
*   Generate document preview without rendering annotations

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-1600 | Implement getting information about lines of text for EmailHtml | Feature |
| ANNOTATIONNET-1599 | Implement getting information about lines of text for Diagrams | Feature |
| ANNOTATIONNET-1598 | Implement getting information about lines of text for Cells | Feature |
| ANNOTATIONNET-1597 | Implement getting information about lines of text for Slides | Feature |
| ANNOTATIONNET-1596 | Implement getting information about lines of text for PDF | Feature |
| ANNOTATIONNET-1642 | Generate document preview without rendering annotations | Feature |

## Public API and Backward Incompatible Changes


### 1. Generate document preview without rendering annotations

Since this update you are able to generate documents preview without rendering annotations on it.

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"D:/result_{pageNumber}.png";
        return File.Create(pagePath);
    });

    previewOptions.RenderAnnotations = false;

    annotator.Document.GeneratePreview(previewOptions);
}
```
#
To get more information about preview generation, please visit this [page](https://docs.groupdocs.com/annotation/net/generate-document-pages-preview/).

### 2. Implemented generation of text information for each page

Since this update you are able to get information about documents text content. [PageInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) structure was changed and now it contains information not only about page width and height, but also about it's text content. To learn how to use this feature please visit [this](https://docs.groupdocs.com/annotation/net/document-text-info/) page.
