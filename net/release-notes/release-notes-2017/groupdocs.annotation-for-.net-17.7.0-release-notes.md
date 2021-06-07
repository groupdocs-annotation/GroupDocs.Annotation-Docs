---
id: groupdocs-annotation-for-net-17-7-0-release-notes
url: annotation/net/groupdocs-annotation-for-net-17-7-0-release-notes
title: GroupDocs.Annotation for .NET 17.7.0 Release Notes
weight: 5
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 17.7.0{{< /alert >}}

## Major Features

Below the list of  new features and fixed bugs in this regular monthly release of GroupDocs.Annotation for .NET. The most notable are:

*   Fixed SVG path parsing for specific cases
*   Implemented annotations import for Diagrams format (Area Redaction, Polyline, Text Field, Area Redaction)
*   Implemented setting opacity to annotations where it is possible
*   Exceptions handling improvements (added several more specific type of exceptions)

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-448 | Set opacity for Diagrams annotations | New Feature |
| ANNOTATIONNET-447 | Set opacity for Pdf annotations | New Feature |
| ANNOTATIONNET-446 | Set opacity for Words annotations | New Feature |
| ANNOTATIONNET-445 | Set opacity for Slides annotations | New Feature |
| ANNOTATIONNET-442 | Implement additional specific exceptions | Improvement |
| ANNOTATIONNET-441 | Import text field annotation from Diagram | New Feature |
| ANNOTATIONNET-440 | Import polyline annotation from Diagram | New Feature |
| ANNOTATIONNET-439 | Import Area Redaction annotation from diagram | New Feature |
| ANNOTATIONNET-438 | Import area annotation from diagram | New Feature |
| ANNOTATIONNET-430 | Implement import annotations for Diagram | New Feature |
| ANNOTATIONNET-421 | Bug with parsing specific SVG path | Bug |
| ANNOTATIONNET-419 | Implement TextField annotation for Diagrams | New Feature |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 17.7.0. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

#### How to use Opacity
    
```csharp
// 1. To AnnotationInfo object added new Opacity field that sets opacity of annotation (can be null or float number between 0 and 1)

	public double? Opacity { get; set; }


// 2. Text annotation.
AnnotationInfo textAnnotation = new AnnotationInfo
{
    Box = new Rectangle(68, 154, 102, 9),
    PageNumber = 0,
    SvgPath = "[{\"x\":68.7886,\"y\":687.5769},{\"x\":170.8186,\"y\":687.5769},{\"x\":68.7886,\"y\":678.5769},{\"x\":170.8186,\"y\":678.5769}]",
    Type = AnnotationType.Text,
    CreatorName = "Anonym A."
    CreatorName = "Anonym A.",
	Opacity = 0.1
};
```
    
#### Import annotations from Diagram documents
    
```csharp
using System.IO;
using System.Linq;
using System.Reflection;
using GroupDocs.Annotation;
using GroupDocs.Annotation.Config;
using GroupDocs.Annotation.Domain;
using GroupDocs.Annotation.Handler;
namespace ImportAnnotationsDiagram
{
    class Program
    {
        static void Main(string[] args)
        {
            AnnotationConfig cfg = new AnnotationConfig();
            cfg.StoragePath = "StorageFolder";
            AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);
            if (!Directory.Exists(cfg.StoragePath))
            {
                Directory.CreateDirectory(cfg.StoragePath);
            }
            new License().SetLicense(@"path_to_licence");
            Stream input = new FileStream("../../testImportArrow.vsdx", FileMode.Open,FileAccess.ReadWrite); 
 
            AnnotationInfo[] annotations = annotator.ImportAnnotations(input, DocumentType.Diagram);
            Stream clearDocument = new FileStream("../../testClear.vsd", FileMode.Open,FileAccess.ReadWrite); 
            Stream output = annotator.ExportAnnotationsToDocument(clearDocument, annotations.ToList(), DocumentType.Diagram);

            using (FileStream fileStream = new FileStream("../../testDiagramExported.vsdx", FileMode.Create))
            {
                byte[] buffer = new byte[output.Length];
                output.Seek(0L, SeekOrigin.Begin);
                output.Read(buffer, 0, buffer.Length);
                fileStream.Write(buffer, 0, buffer.Length);
                fileStream.Close();
            }
        }
    }
}
```
