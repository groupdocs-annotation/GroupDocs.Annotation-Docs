---
id: groupdocs-annotation-for-net-17-3-0-release-notes
url: annotation/net/groupdocs-annotation-for-net-17-3-0-release-notes
title: GroupDocs.Annotation for .NET 17.3.0 Release Notes
weight: 9
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 17.3.0{{< /alert >}}

## Major Features

Below the list of  new features and fixed bugs in this regular monthly release of GroupDocs.Annotation for .NET. The most notable are:

Implemented annotations annotating documents of following types:

*   Adding annotations to EMF/WMF documents
*   Added Distance Annotations to image documents
*   Implemented CAD documents annotating 
*   Implemented Arrow annotation for images
*   Fixed replies to annotations for Word documents

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-368 | Implement distance annotation for images | New Feature |
| ANNOTATIONNET-367 | Implement annotating EMF/WMF document | New Feature |
| ANNOTATIONNET-365 | Export to MS-Word exporting the repeated reply comments | Bug |
| ANNOTATIONNET-363 | Implement CAD documents annotating | New Feature |
| ANNOTATIONNET-361 | Implement adding Arrow annotation to Image documents | New Feature |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 17.3.0. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

### DjVu

DjVu files after the annotation has been added will be saved to PDF file format:

```csharp
List<AnnotationInfo> annotations = new List<AnnotationInfo>();

AnnotationConfig cfg = new AnnotationConfig();
cfg.StoragePath = "StorageFolder";

AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);
AnnotationInfo pointAnnotation = new AnnotationInfo()
{
	PageNumber = 5,
	Type = AnnotationType.Point,
	Box = new Rectangle(100, 100, 0, 0),
	FieldText = "Hello!",
	CreatorName = "John"
};

annotations.Add(pointAnnotation);

Stream cleanImage = Assembly.GetExecutingAssembly().GetManifestResourceStream("0.djvu");

//result is PDF file
Stream result = annotator.ExportAnnotationsToDocument(cleanImage, annotations, DocumentType.Images);

using (FileStream fileStream = new FileStream("Annotated.pdf"),FileMode.Create))
{
	byte[] buffer = new byte[result.Length];
	result.Seek(0, SeekOrigin.Begin);
	result.Read(buffer, 0, buffer.Length);
	fileStream.Write(buffer, 0, buffer.Length);
}
```

### DICOM

DICOM-files after the annotation has been added will be saved to BMP file:

```csharp
List<AnnotationInfo> annotations = new List<AnnotationInfo>();


AnnotationConfig cfg = new AnnotationConfig();
cfg.StoragePath = "StorageFolder";


AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);

AnnotationInfo pointAnnotation = new AnnotationInfo()
{
	PageNumber = 0,
	Type = AnnotationType.Point,
	Box = new Rectangle(100, 100, 0, 0),
	FieldText = "Hello!",
	CreatorName = "John"
};

annotations.Add(pointAnnotation);

Stream cleanImage = Assembly.GetExecutingAssembly().GetManifestResourceStream("0.dcm");

//result as bmp file
Stream result = annotator.ExportAnnotationsToDocument(cleanImage, annotations, DocumentType.Images);


using (FileStream fileStream = new FileStream("Annotated.bmp"),FileMode.Create))
{
	byte[] buffer = new byte[result.Length];
	result.Seek(0, SeekOrigin.Begin);
	result.Read(buffer, 0, buffer.Length);
	fileStream.Write(buffer, 0, buffer.Length);
}
```

### CAD-files (DWG)

CAD-files after the annotation has been added will be saved to BMP file:

```csharp
List<AnnotationInfo> annotations = new List<AnnotationInfo>();


AnnotationConfig cfg = new AnnotationConfig();
cfg.StoragePath = "StorageFolder";


AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);


AnnotationInfo distanceAnnotation = new AnnotationInfo()

{
	CreatedOn = DateTime.Now,
    Type = AnnotationType.Distance,
    Box = new Rectangle(20, 20, 250, 250),
    BackgroundColor = -15988609,
    Text = "500px",
    FontFamily = "Arial"
};
annotations.Add(distanceAnnotation);

Stream cleanImage = Assembly.GetExecutingAssembly().GetManifestResourceStream("0.dwg");

//result as bmp file
Stream result = annotator.ExportAnnotationsToDocument(cleanImage, annotations, DocumentType.Images);


using (FileStream fileStream = new FileStream("Annotated.bmp"),FileMode.Create))
{
	byte[] buffer = new byte[result.Length];
	result.Seek(0, SeekOrigin.Begin);
	result.Read(buffer, 0, buffer.Length);
	fileStream.Write(buffer, 0, buffer.Length);
}
```

### EMF/WMF

EMF/WMF-files after the annotation has been added will be saved to PNG files:

```csharp
List<AnnotationInfo> annotations = new List<AnnotationInfo>();


AnnotationConfig cfg = new AnnotationConfig();
cfg.StoragePath = "StorageFolder";


AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);


AnnotationInfo distanceAnnotation = new AnnotationInfo()

{
	CreatedOn = DateTime.Now,
    Type = AnnotationType.Distance,
    Box = new Rectangle(20, 20, 250, 250),
    BackgroundColor = -15988609,
    Text = "500px",
    FontFamily = "Arial"
};
annotations.Add(distanceAnnotation);

Stream cleanImage = Assembly.GetExecutingAssembly().GetManifestResourceStream("0.wmf");

//result as bmp file
Stream result = annotator.ExportAnnotationsToDocument(cleanImage, annotations, DocumentType.Images);


using (FileStream fileStream = new FileStream("Annotated.png"),FileMode.Create))
{
	byte[] buffer = new byte[result.Length];
	result.Seek(0, SeekOrigin.Begin);
	result.Read(buffer, 0, buffer.Length);
	fileStream.Write(buffer, 0, buffer.Length);
}
```
