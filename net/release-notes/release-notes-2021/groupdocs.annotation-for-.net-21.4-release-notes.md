---
id: groupdocs-annotation-for-net-21-4-release-notes
url: annotation/net/groupdocs-annotation-for-net-21-4-release-notes
title: GroupDocs.Annotation for .NET 21.4 Release Notes
weight: 90
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---

{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 21.4{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 21.4:
*   Refactored and simplified Core logic of the project
*   Improved mechanism of ducment type detection when passing FileStream
*   Fixed overflow exception while getting document information for diagrams
*   Fixed issue with saving .dwg and .dxf files
*   Fixed issue with license applying for GroupDocs.Annotation-for-.NET-MVC example project

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-1648 | Refactoring and simplifying Core logic | Improvement |
| ANNOTATIONNET-1650 | Try map document type by file extension when FileStream is passed | Improvement |
| ANNOTATIONNET-1651 | Problems related to reading DocumentInfo and adding annotations for some of the .vsd files. | Bug |
| ANNOTATIONNET-1652 | Problem on processing .dwg and .dxf files in WebApp | Bug |
| ANNOTATIONNET-1656 | License is not applied | Bug |



## Public API and Backward Incompatible Changes

1. During the complete code simplifying and refactoring, namespaces for the public API were changed. Therefore, since 21.4 the [License](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.licenses/license) and [Metered](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.licenses/metered) classes, which were previously located in [GroupDocs.Annotation](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation) namespace, have been moved to a separate namespace [GroupDocs.Annotation.Licenses](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.licenses).