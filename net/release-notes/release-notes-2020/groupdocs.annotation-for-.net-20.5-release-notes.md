---
id: groupdocs-annotation-for-net-20-5-release-notes
url: annotation/net/groupdocs-annotation-for-net-20-5-release-notes
title: GroupDocs.Annotation for .NET 20.5 Release Notes
weight: 80
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 20.5{{< /alert >}}

## Major Features

Below the list of most notable changes in  release of GroupDocs.Annotation for .NET 20.5:

*   Implemented managing different versions of annotated documents for Images and Diagrams
*   Implemented additional overloads for Save method without filestream
*   Fixed background opacity for PNG files
*   Fixed issue with PagesInfo for Excel files in MVC project
*   Fixed clearing comments for Excel files
*   Fixed unable to Save document as file that was used to create annotator


Full List of Issues Covering all Changes in this Release 

| Key | Summary | Type |
| --- | --- | --- |
| ANNOTATIONNET-1292 | Implement managing different versions of annotated documents for Diagrams | Feature |
| ANNOTATIONNET-1291 | Implement managing different versions of annotated documents for Images | Feature |
| ANNOTATIONNET-1369 | Add overloads for Annotator.Save method without stream or filepath | Improvement |
| ANNOTATIONNET-1370 | Adding annotations to PNG image makes background non transparent | Bug |
| ANNOTATIONNET-1368 | Unable to Save document as file that was used to create annotator | Bug |
| ANNOTATIONNET-1367 | A generic error occurred in GDI+ when processing Slides documents | Bug |
| ANNOTATIONNET-1362 | TextAnnotations not cleaning in Cells after adding Versions | Bug |
| ANNOTATIONNET-1361 | Comments not cleaned in Excel files | Bug |
| ANNOTATIONNET-1358 | Wrong file metadata issue in Images after adding Versions | Bug |
| ANNOTATIONNET-1357 | Empty PagesInfo for Excel file in MVC project. | Bug |

## Public API and Backward Incompatible Changes

Starting from version 20.5 several Save methods overloads was added for user convenience

Now you can call Empty Save to save documents as input file for annotator. If you need to add some options, you may call Save method with only one parameter - SaveOptions, it will do the same as empty but will consider your options.

1) Method accepts SaveOption parameter

```csharp
using (FileStream fs = new FileStream(_resultPath, FileMode.Open))
{
	using (Annotator annotator = new Annotator(fs))
	{
		annotator.Save(new SaveOptions { Version = "1" });
	}
}
```

```csharp
using (Annotator annotator = new Annotator(_resultPath))
{
    annotator.Save(new SaveOptions { Version = "1" });
}
```

2) Empty Save Method

```csharp
using (FileStream fs = new FileStream(_resultPath, FileMode.Open))
{
	using (Annotator annotator = new Annotator(fs))
	{
		annotator.Save();
	}
}
```

```csharp
using (Annotator annotator = new Annotator(_resultPath))
{
    annotator.Save();
}
```
