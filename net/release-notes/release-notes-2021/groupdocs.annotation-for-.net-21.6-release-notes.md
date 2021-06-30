---
id: groupdocs-annotation-for-net-21-6-release-notes
url: annotation/net/groupdocs-annotation-for-net-21-6-release-notes
title: GroupDocs.Annotation for .NET 21.6 Release Notes
weight: 70
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 21.6{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 21.6:
*   Updated information about supported types
*   Moved License and Metered class to GroupDocs.Annotation namespace
*   Fixed issue with counting page for PPT file
*   Added an ability to generate preview in different formats for CAD document
*   Fixed problem with closing a stream when saving a tiff file
*   Fixed exception on adding watermarks to pdf without license

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-1727 | Generate preview for CAD using PreviewFormat | Feature |
| ANNOTATIONNET-1684 | Match supported formats | Improvement |
| ANNOTATIONNET-1718 | Move License and Metered classes to GroupDocs.Annotation namespace | Improvement |
| ANNOTATIONNET-1712 | 'Image loading failed.' error during repetitive reading the TIFF-file content. | Bug |
| ANNOTATIONNET-1713 | Zero pages count in PPT-file info. | Bug |
| ANNOTATIONNET-1720 | Exception on adding watermarks to pdf without license | Bug |
| ANNOTATIONNET-1724 | Problem closing a stream when saving a tiff file | Bug |
| ANNOTATIONNET-1726 | Pages count 0 for PowerPoint document | Bug |
| ANNOTATIONNET-1747 | PPS file detects as PPT | Bug |

## Public API and Backward Incompatible Changes

### 1. Moved License and Metered class to GroupDocs.Annotation namespace

Class License and Metered were moved to [GroupDocs.Annotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation) namespace. The whole [GroupDocs.Annotation.Licenses](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.licenses) namespace became obsolete and will be removed soon. Please use these class from the new namespace.


### 2. List of supported formats have been tidied up

The list of supported formats from [documentation](https://docs.groupdocs.com/annotation/net/supported-document-formats/) and those available with [GetSupportedFileTypes](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/filetype/methods/getsupportedfiletypes) method have been given into accordance.
