---
id: groupdocs-annotation-for-net-17-2-0-release-notes
url: annotation/net/groupdocs-annotation-for-net-17-2-0-release-notes
title: GroupDocs.Annotation for .NET 17.2.0 Release Notes
weight: 10
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 17.2.0{{< /alert >}}

## Major Features

Below the list of improvements  and new features in this regular monthly release of GroupDocs.Annotation for .NET. The most notable are:

Implemented annotations annotating documents of following types:

*   Add Metered licensing support
*   Implemented DICOM documents annotating 
*   Implemented Otp documents annotating 
*   Implemented DjVu documents annotating 

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-351 | Implement annotating for DICOM format images | New Feature |
| ANNOTATIONNET-348 | Add Metered licensing support | New Feature |
| ANNOTATIONNET-344 | Implement adding annotations to Otp format | New Feature |
| ANNOTATIONNET-340 | Implement annotating DjVu format | New Feature |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 17.2.0. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

### Metered licensing

```csharp
var storagePath = "StoragePath";
// Setup Annotation configuration
var annotationConfig = new AnnotationConfig { StoragePath = storagePath };
Stream cleanPdf = Assembly.GetExecutingAssembly().GetManifestResourceStream("SetLicense.TestData.Clear.pdf");
            
// Create new instance of GroupDocs.Annotation.Metered classs
GroupDocs.Annotation.Metered metered = new GroupDocs.Annotation.Metered();
            
// Set public and private key to metered instance
metered.SetMeteredKey("***", "***");
            
// Get metered value before usage of the annotation
decimal amountBefore = GroupDocs.Annotation.Metered.GetConsumptionQuantity();
Console.WriteLine("Amount consumed  before: " + amountBefore);
            
//instantiating the annotation handler
AnnotationImageHandler annotator = new AnnotationImageHandler(annotationConfig);
AnnotationInfo pointAnnotation = new AnnotationInfo
{
	AnnotationPosition = new Point(852.0, 81.0),
	Box = new Rectangle(212f, 81f, 142f, 0.0f),
	PageNumber = 0,
	Type = AnnotationType.Point,
	CreatorName = "Anonym A."
};
            
Stream result = annotator.ExportAnnotationsToDocument(cleanPdf, new List<AnnotationInfo>{ pointAnnotation}, DocumentType.Pdf);
// Get metered value after usage of the annotation
decimal amountAfter = GroupDocs.Annotation.Metered.GetConsumptionQuantity();
Console.WriteLine("Amount consumed  after: " + amountAfter);
Console.WriteLine("Press any key...");
Console.ReadKey();
```
