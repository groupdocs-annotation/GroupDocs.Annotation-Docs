---
id: groupdocs-annotation-for-net-3-1-0-release-notes
url: annotation/net/groupdocs-annotation-for-net-3-1-0-release-notes
title: GroupDocs.Annotation for .NET 3.1.0 Release Notes
weight: 6
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 3.1.0{{< /alert >}}

## Major Features

This is the version of new generation GroupDocs.Annotation for .NET. The most notable features are:

*   Added ability of native annotating Words documents
*   Improved performance of document Viewing
*   Added ability to export annotated Words documents

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Category |
| --- | --- | --- |
| ANNOTATIONNET-196 | Implement getting not all pages of document at once (performance improvenet) | Improvement |
| ANNOTATIONNET-197 | Increase slow Performance on big file | Improvement |
| ANNOTATIONNET-216 | Implement proper exception for unsuported annotations for Slides and Cells formats | Improvement |
| ANNOTATIONNET-189 | Implement ResourceRedaction annotation in Word documents | New Feature |
| ANNOTATIONNET-191 | Implement Strikeout annotation in Word documents | New Feature |
| ANNOTATIONNET-190 | Implement TextField annotation in Word documents | New Feature |
| ANNOTATIONNET-187 | Implement Text Replacement in Words documents (comments) | New Feature |
| ANNOTATIONNET-188 | Implement TextHighlight annotation in Word documents | New Feature |
| ANNOTATIONNET-211 | Implement Text Area annotatoin in Words documents | New Feature |
| ANNOTATIONNET-213 | Update open-source WebUI sample to use GroupDocs.Annotation 3.1.0 | New Feature |
| ANNOTATIONNET-198 | Implement document export to Word | New Feature |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 3.1.0. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

Example of creating Annotations of different types (for Words format) Skip to end of metadata

### Text Annotation



```csharp
            AnnotationInfo textAnnotation = new AnnotationInfo
            {
                PageNumber = 0,
                SvgPath = "[{\"x\":186.698,\"y\":706.196},{\"x\":318.41201,\"y\":706.196},{\"x\":186.698,\"y\":697.196},{\"x\":318.41201,\"y\":697.196}]",
                Type = AnnotationType.Text
            };

```

### Area Annnotation



```csharp
            AnnotationInfo areaAnnnotation = new AnnotationInfo
            {
                BackgroundColor = 11111111,
                Box = new Rectangle(87.9f, 276.5f, 435.7f, 87f),
                PageNumber = 0,
                Type = AnnotationType.Area
            };

```

### Strikeout Annotation



```csharp
            AnnotationInfo strikeoutAnnotation = new AnnotationInfo
            {
                Box = new Rectangle(87.9f, 276.5f, 435.7f, 87f),
                PageNumber = 0,
                PenColor = 1201033,
                SvgPath = "[{\"x\":208.392,\"y\":313.088},{\"x\":519.659,\"y\":313.088},{\"x\":208.392,\"y\":304.088},{\"x\":519.659,\"y\":304.088}]",
                Type = AnnotationType.TextStrikeout
            };

```

### Text Field Annotation



```csharp
            AnnotationInfo textFieldAnnotation = new AnnotationInfo
            {
                FieldText = "text in the box",
                FontFamily = "Arial",
                FontSize = 10,
                Box = new Rectangle(92f, 73f, 106f, 45f),
                PageNumber = 1,
                Type = AnnotationType.TextField,
            };

```

### Text Replacement Annotation



```csharp
            AnnotationInfo textReplacementAnnotation = new AnnotationInfo
            {
                FieldText = " \"REPLACED TEXT\" ",
                FontSize = 10,
                SvgPath = "[{\"x\":251.224,\"y\":637.20401},{\"x\":327.89,\"y\":637.20401},{\"x\":251.224,\"y\":628.20401},{\"x\":327.89,\"y\":628.20401}]",
                PageNumber = 0,
                Type = AnnotationType.TextReplacement,
            };

```

### Arrow Annotation



```csharp
            AnnotationInfo arrowAnnotation = new AnnotationInfo
            {
                Box = new Rectangle(479f, 218f, -261f, -89f),
                PageNumber = 0,
                Type = AnnotationType.Arrow,
            };

```

### Text Redaction Annotation



```csharp
            AnnotationInfo textRedactionAnnotation = new AnnotationInfo
            {
                PageNumber = 1,
                SvgPath = "[{\"x\":72,\"y\":676.07},{\"x\":196.427,\"y\":676.074},{\"x\":72,\"y\":662.674},{\"x\":196.427,\"y\":662.674}]",
                Type = AnnotationType.TextRedaction,
            };

```

### Resource Redaction Annotation



```csharp
            AnnotationInfo resourceRedactionAnnotation = new AnnotationInfo
            {
                Box = new Rectangle(69f, 337f, 449f, 118f),
                PageNumber = 1,
                Type = AnnotationType.ResourcesRedaction,
            };


```

### Underline Annotation



```csharp
            AnnotationInfo underlineAnnotation = new AnnotationInfo
            {
                PageNumber = 1,
                SvgPath = "[{\"x\":415.17499,\"y\":628.874},{\"x\":511.85101,\"y\":628.874},{\"x\":415.17499,\"y\":619.874},{\"x\":511.85101,\"y\":619.874}]",
                Type = AnnotationType.TextUnderline
            };

```
