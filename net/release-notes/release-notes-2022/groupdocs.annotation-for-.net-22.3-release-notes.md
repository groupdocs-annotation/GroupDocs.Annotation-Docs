---
id: groupdocs-annotation-for-net-22-3-release-notes
url: annotation/net/groupdocs-annotation-for-net-22-3-release-notes
title: GroupDocs.Annotation for .NET 22.3 Release Notes
weight: 20
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 22.3{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 22.3:
* Fixed Replacement annotation is added as a Strikeout annotation in PDF.
* Added ability to change font size for Replacement annotation.


## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-1961 | Fixed adding replacement annotation as Strikeout to PDF document | Bug |
| ANNOTATIONNET-1982 | Implement the ability to add font size for Replacement annotation | Feature |


## Public API and Backward Incompatible Changes

1. Added ability to change font size for Replacement annotation, you could find full example [here](https://docs.groupdocs.com/annotation/net/add-replacement-annotation/)
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ReplacementAnnotation replacement = new ReplacementAnnotation
    {
	FontSize = 11,
	//other propeties
    };
    annotator.Add(replacement);
    annotator.Save("result.pdf");
}
```
