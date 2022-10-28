---
id: groupdocs-annotation-for-net-21-8-release-notes
url: annotation/net/groupdocs-annotation-for-net-21-8-release-notes
title: GroupDocs.Annotation for .NET 21.8 Release Notes
weight: 50
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---

{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 21.8{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 21.8:
* Implemented ability to auto scale Watermark depending on the length of the string for all most popular supported document formats.


## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-1783 | Auto scale Watermark string depending on the length of the string for PDF documents | Feature |
| ANNOTATIONNET-1782 | Auto scale Watermark string depending on the length of the string for Images document | Feature |
| ANNOTATIONNET-1781 | Auto scale Watermark string depending on the length of the string for Cells document | Feature |
| ANNOTATIONNET-1780 | Auto scale Watermark string depending on the length of the string for Slides document | Feature |
| ANNOTATIONNET-1779 | Auto scale Watermark string depending on the length of the string for Diagrams document | Feature |
| ANNOTATIONNET-1778 | Auto scale Watermark string depending on the length of the string for Word document | Feature |


## Public API and Backward Incompatible Changes

### 1. Ability to customize watermark for automatic scaling

In version 21.8 we have added a auto scaling for watermark, that allows watermark string to auto scale depending on the length of the string. To learn more about this auto scale follow this [link](https://docs.groupdocs.com/watermark/net/).
```csharp
WatermarkAnnotation watermark = new WatermarkAnnotation
    {
        Angle = 75,
        Box = new Rectangle(200, 200, 100, 50),
        CreatedOn = DateTime.Now,
        Text = "Watermark",
        FontColor = 65535,
        FontSize = 12,
        Message = "This is watermark annotation",
        Opacity = 0.7,
        Replies = new List<Reply>
        {
            new Reply
            {
                Comment = "First comment",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
                Comment = "Second comment",
                RepliedOn = DateTime.Now
            }
        }
    };
    watermark.AutoScale = true;// watermark will be auto scaled according to string length
    annotator.Add(watermark);
```