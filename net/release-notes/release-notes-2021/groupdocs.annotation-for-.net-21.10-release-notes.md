---
id: groupdocs-annotation-for-net-21-10-release-notes
url: annotation/net/groupdocs-annotation-for-net-21-10-release-notes
title: GroupDocs.Annotation for .NET 21.10 Release Notes
weight: 30
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---

{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 21.10{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 21.10:
* Implemented ability to add Link annotation background color.
* Implemented ability to add Underline annotation background color (except Diagram documents).
* Implemented ability to add Strikeout annotation background color (except Diagram documents).
* Implemented ability to change color of Text Redaction annotation.


## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-1843 | Add Background color for annotations (Undreline, Strikeout) that not have it in the Word | Improvement |
| ANNOTATIONNET-1844 | Add Background color for annotations that not have it in the Diagrams | Improvement |
| ANNOTATIONNET-1845 | Add Background color for annotations (Undreline, Strikeout) that not have it in the PDF | Improvement |
| ANNOTATIONNET-1846 | Add Background color for annotations (Link, Underline, Strikeout) that not have it in the Slides | Improvement |
| ANNOTATIONNET-1842 | Add Background color for annotations (Link, Underline, Strikeout) that not have it in the Cells  | Improvement |
| ANNOTATIONNET-1847 | Implement ability to change color Text Redaction annotation | Improvement |


## Public API and Backward Incompatible Changes

### 1. From version 21.10 could set background color via setting `BackgroundColor` for the listed annotations. 
* [LinkAnnotation](https://docs.groupdocs.com/annotation/net/add-link-annotation/).
* [StrikeoutAnnotation](https://docs.groupdocs.com/annotation/net/add-annotation-to-the-document/).
* [UnderlineAnnotation](https://docs.groupdocs.com/annotation/net/add-underline-annotation/)
          