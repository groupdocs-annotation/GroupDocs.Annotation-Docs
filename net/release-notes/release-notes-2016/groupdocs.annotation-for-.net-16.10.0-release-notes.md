---
id: groupdocs-annotation-for-net-16-10-0-release-notes
url: annotation/net/groupdocs-annotation-for-net-16-10-0-release-notes
title: GroupDocs.Annotation for .NET 16.10.0 Release Notes
weight: 3
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 16.10.0{{< /alert >}}

## Major Features

Below the list of improvements fixes and new features in this regular monthly release of GroupDocs.Annotation for .NET. The most notable are:

*   Implemented following for slides documents:
*    Point annotation
*   Area annotation
*   Resource Redaction annotation
*   Arrow annotation
*   TextField annotation
*   Polyline annotation
*   Watermark annotation
*   Show and store annotation author when export annotation for PDF documents

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Category |
| --- | --- | --- |
| ANNOTATIONNET-282 | Implement Watermark annotation for Slides format | New Feature |
| ANNOTATIONNET-276 | Implement Area annotation for Slides format | New Feature |
| ANNOTATIONNET-275 | Implement Arrow annotation for Slides format | New Feature |
| ANNOTATIONNET-273 | Implement Text Field annotation in Slides document | New Feature |
| ANNOTATIONNET-272 | Implement Polyline annotation for Slides format | New Feature |
| ANNOTATIONNET-271 | Implement Point annotation for Slides format | New Feature |
| ANNOTATIONNET-266 | Show and store annotation author when export annotation for PDF documents | Improvement |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 16.10.0. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}



```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Reflection;
using GroupDocs.Annotation;
using GroupDocs.Annotation.Config;
using GroupDocs.Annotation.Domain;
using GroupDocs.Annotation.Handler;


namespace AddAnnotationsSlides
{
    class Program
    {
        static void Main(string[] args)
        {
            List<AnnotationInfo> annotations;
            AnnotationConfig cfg = new AnnotationConfig();
            cfg.StoragePath = "StorageFolder";

            AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);
            new License().SetLicense("proper_path_to_license");
            Stream cleanPresentation =  new FileStream("../../AddAnnotationsSlides.TestData.testSlides.pptx", FileMode.Open,FileAccess.ReadWrite);
            annotations = new List<AnnotationInfo>();


            AnnotationInfo pointAnnotation = new AnnotationInfo()
            {
                PageNumber = 0,
                Type = AnnotationType.Point,
                Box = new Rectangle(100, 100, 0, 0),
                FieldText = "Hello!",
                CreatorName = "John"
            };
            AnnotationInfo areaAnnotation = new AnnotationInfo()
            {
                CreatedOn = DateTime.Now,
                Type = AnnotationType.Area,
                PageNumber = 0,
                Box = new Rectangle(100, 72.7f, 50, 50),
                BackgroundColor = -15988609
            };
            AnnotationInfo arrowAnnotation = new AnnotationInfo()
            {
                Type = AnnotationType.Arrow,
                CreatedOn = DateTime.Now,
                PageNumber = 0,
                Box = new Rectangle(0, 0, 100, 100),
                BackgroundColor = 15988609
            };
            AnnotationInfo polylineAnnotation = new AnnotationInfo()
            {
                Type = AnnotationType.Polyline,
                CreatedOn = DateTime.Now,
                Box = new Rectangle((float)250.82807922363281, (float)35.632957458496094, (float)102.70676422119141, (float)12.576337814331055),
                PageNumber = 0,
                PenColor = 65015,
                SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l0.6986854460093896,0l0.6986854460093896,-1.3973708920187793l1.3973708920187793,
-0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,-1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,
-0.6986854460093896l1.3973708920187793,-1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,
-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0,
-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.096056338028169,
-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,
0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,
0l1.3973708920187793,0l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,
0l0.6986854460093896,0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,
0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,0.6986854460093896l1.3973708920187793,
0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,
0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,
0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,0l0.6986854460093896,
0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
            };

            AnnotationInfo resourceRedactionAnnotation = new AnnotationInfo()
            {
                CreatedOn = DateTime.Now,
                Type = AnnotationType.ResourcesRedaction,
                PageNumber = 0,
                Box = new Rectangle(100, 72.7f, 50, 50)
            };

            AnnotationInfo textFieldAnnotation = new AnnotationInfo()
            {
                CreatedOn = DateTime.Now,
                Type = AnnotationType.TextField,
                PageNumber = 0,
                Box = new Rectangle(100, 72.7f, 50, 50),
                FontColor = -15988609,
                FieldText = "some text",
                FontFamily = "times new roman"
            };

            AnnotationInfo watermarkAnnotation = new AnnotationInfo()
            {
                CreatedOn = DateTime.Now,
                Type = AnnotationType.Watermark,
                FieldText = "This is watermark",
                FontFamily = "arial",
                Box = new Rectangle(100,50,50,0),
                FontSize = 25,
                FontColor = -15988609
            };

            annotations.Add(pointAnnotation);
            annotations.Add(areaAnnotation);
            annotations.Add(arrowAnnotation);
            annotations.Add(resourceRedactionAnnotation);
            annotations.Add(polylineAnnotation);
            annotations.Add(watermarkAnnotation);
            annotations.Add(textFieldAnnotation);
            Stream result = annotator.ExportAnnotationsToDocument(cleanPresentation, annotations, DocumentType.Slides);
            using(FileStream fileStream = new FileStream("../../Annotated.pptx", FileMode.Create))
            {
                byte[] buffer = new byte[result.Length];
                result.Seek(0, SeekOrigin.Begin);
                result.Read(buffer, 0, buffer.Length);
                fileStream.Write(buffer, 0, buffer.Length);
                fileStream.Close();
            }
        }
    }
}

```
