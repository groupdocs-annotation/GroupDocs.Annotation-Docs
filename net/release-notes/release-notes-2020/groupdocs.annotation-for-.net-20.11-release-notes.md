---
id: groupdocs-annotation-for-net-20-11-release-notes
url: annotation/net/groupdocs-annotation-for-net-20-11-release-notes
title: GroupDocs.Annotation for .NET 20.11 Release Notes
weight: 38
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 20.11{{< /alert >}}

## Major Features

Below the list of most notable changes in  release of GroupDocs.Annotation for .NET 20.11:

*   Implemented generating of specified worksheet columns for the Cells format
*   Improved Cells generating preview by splitting the worksheet into multiple images
*   Fixed Empty PagesInfo in specific diagram file


Full List of Issues Covering all Changes in this Release 

| Key | Summary | Type |
| --- | --- | --- |
| ANNOTATIONNET-1537 | Investigate the way of displaying huge worksheets of Spreadsheet | Improvement |
| ANNOTATIONNET-1514 | Incorrect image size for Excel document | Bug |
| ANNOTATIONNET-1540 | PagesInfo is empty | Bug |

## Public API and Backward Incompatible Changes

New [WorksheetColumns](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/worksheetcolumns) property in [PreviewOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions) class that allows to specify the range of generated columns on a specified worksheet.

Example how to use it:
```csharp
PreviewOptions previewOptions =
    new PreviewOptions(pageNumber => new FileStream($"preview_pages/page{pageNumber}.png", FileMode.Create),
        (number, stream) => stream.Dispose());
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 2, 3));
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 1, 1));

using (Annotator annotator = new Annotator("input.xlsx"))
{
    annotator.Document.GeneratePreview(previewOptions);
}
```