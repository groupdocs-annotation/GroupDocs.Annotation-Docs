---
id: groupdocs-annotation-for-net-20-9-release-notes
url: annotation/net/groupdocs-annotation-for-net-20-9-release-notes
title: GroupDocs.Annotation for .NET 20.9 Release Notes
weight: 40
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 20.9{{< /alert >}}

## Major Features

Below the list of most notable changes in  release of GroupDocs.Annotation for .NET 20.9:

*   Improved adding ImageAnnotation functionality
*   Fixed exception while processing specific xlsx files
*   Fixed exception while annotating email files
*   Fixed issue with streams when Save method invoked
*   Fixed Replacement annotation on Words files


Full List of Issues Covering all Changes in this Release 

| Key | Summary | Type |
| --- | --- | --- |
| ANNOTATIONNET-1482 | Replace file ImageAnnotation functionality with streams | Improvement |
| ANNOTATIONNET-1392 | Replacement annotation damages words file | Bug |
| ANNOTATIONNET-1485 | CorruptedOrDamagedFileException on opening xlsx files | Bug |
| ANNOTATIONNET-1486 | Method Annotator.Save returns closed stream | Bug |
| ANNOTATIONNET-1487 | Can't get document info for msg file | Bug |
| ANNOTATIONNET-1488 | NullReferenceException when annotating e-mail | Bug |

## Public API and Backward Incompatible Changes
Removed the deprecated ImportAnnotations property from the LoadOptions class because annotations are imported automatically.

So, if before version 20.9 this code was correct:

```csharp
Annotator annotator = new Annotator("input.docx", new LoadOptions { Password = "password", ImportAnnotations = true });
```
#
Beginning with version 20.9, LoadOptions no longer has the ImportAnnotations property. The previous code needs to be changed. Example:


```csharp
Annotator annotator = new Annotator("input.docx", new LoadOptions { Password = "password" });
```