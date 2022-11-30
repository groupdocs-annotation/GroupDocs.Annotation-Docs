---
id: groupdocs-annotation-for-net-22-11-release-notes
url: annotation/net/groupdocs-annotation-for-net-22-11-release-notes
title: GroupDocs.Annotation for .NET 22.11 Release Notes
weight: 60
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 22.11{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 22.11:
* Added the ability to add roles with restrictions to comments.
* Fixed incorrect behavior when getting EMLX and PDF info document.
* Fixed FileNotFoundException when saving pdf file into stream


## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
|ANNOTATIONNET-2113 | Add user roles with restrictions to comments | Feature |
|ANNOTATIONNET-2106 | FileNotFoundException when saving pdf file into stream | Bug |
|ANNOTATIONNET-2105 | Fix exception when getting info about emlx document | Bug |
|ANNOTATIONNET-2104 | Fix getting info document returns null FileType for pdf document | Bug |



## Public API and Backward Incompatible Changes

1. Starting from this version it is possible to specify a user role for each, see example [here](https://docs.groupdocs.com/annotation/net/apply-roles)
