---
id: groupdocs-annotation-for-net-17-1-0-release-notes
url: annotation/net/groupdocs-annotation-for-net-17-1-0-release-notes
title: GroupDocs.Annotation for .NET 17.1.0 Release Notes
weight: 11
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 17.1.0{{< /alert >}}

## Major Features

Below the list of improvements fixes and new features in this regular monthly release of GroupDocs.Annotation for .NET. The most notable are:

Implemented annotations annotating documents of following types:

*   JPG
*   TIFF
*   BMP
*   GIF (static images without animation

Fixed following bugs:

*   When exporting Slide document TextField annotation hasn't text
*   For Slides format fix background when import Resource Redaction annotation 

Improvement:

*   Increase number of integration test for improving quality of product

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-337 | Implement annotating GIF format static images (without animation) | New Feature |
| ANNOTATIONNET-335 | While exporting Slide document TextField annotation hasn't text | Bug |
| ANNOTATIONNET-332 | Implement annotating TIFF format images | New Feature |
| ANNOTATIONNET-331 | Implement annotating BMP format images | New Feature |
| ANNOTATIONNET-329 | Implement annotating JPEG format images | New Feature |
| ANNOTATIONNET-324 | Fix background when import Resource Redaction annotation (for slides) | Bug |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 17.1.0. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

### Example of creating Annotations of different types for Images



```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;
using System.Text;
using System.Threading.Tasks;
using GroupDocs.Annotation;
using GroupDocs.Annotation.Config;
using GroupDocs.Annotation.Domain;
using GroupDocs.Annotation.Handler;

namespace AddAnnotationsImages
{
    class Program
    {
        static void Main(string[] args)
        {
            List<AnnotationInfo> annotations;
            AnnotationConfig cfg = new AnnotationConfig();
            cfg.StoragePath = "StorageFolder";
            AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);

            new License().SetLicense("path_to_proper_license");

            //From version 17.1.0 you can work with images of JPG, TIFF, BMP and GIF(static without animation) format images
            Stream cleanPresentation = Assembly.GetExecutingAssembly().GetManifestResourceStream("AddAnnotationsImages.TestData.0.png");

            annotations = new List<AnnotationInfo>();

            AnnotationInfo textAnnotation = new AnnotationInfo
            {
                Box = new Rectangle(50, 510.9f, 454.73f, 29.08f),
                PageNumber = 0,
                SvgPath = "[{\"x\":200,\"y\":520.92},{\"x\":454.73,\"y\":520.92},{\"x\":200,\"y\":539.98},{\"x\":454.73,\"y\":539.98}]",
                Type = AnnotationType.Text,
                CreatorName = "Anonym A."
            };
            AnnotationInfo textRedactionAnnotation = new AnnotationInfo
            {
                Box = new Rectangle(50, 510.9f, 454.73f, 29.08f),
                PageNumber = 0,
                SvgPath = "[{\"x\":200,\"y\":545.92},{\"x\":454.73,\"y\":545.92},{\"x\":200,\"y\":564.98},{\"x\":454.73,\"y\":564.98}]",
                Type = AnnotationType.TextRedaction,
                CreatorName = "Anonym A."
            };
            AnnotationInfo strikeoutAnnotation = new AnnotationInfo
            {
                Box = new Rectangle(0, 510.92f, 454.73f, 29.08f),
                PageNumber = 0,
                SvgPath = "[{\"x\":120,\"y\":520.92},{\"x\":454.73,\"y\":520.92},{\"x\":120,\"y\":539.98},{\"x\":454.73,\"y\":539.98}]",
                Type = AnnotationType.TextStrikeout,
                CreatorName = "Anonym A."
            };
            AnnotationInfo underlineAnnotation = new AnnotationInfo
            {
                Box = new Rectangle(0, 510.92f, 454.73f, 29.08f),
                PageNumber = 0,
                SvgPath = "[{\"x\":120,\"y\":520.92},{\"x\":454.73,\"y\":520.92},{\"x\":120,\"y\":539.98},{\"x\":454.73,\"y\":539.98}]",
                Type = AnnotationType.TextUnderline,
                CreatorName = "Anonym A."
            };
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
                Box = new Rectangle(200, 72.7f, 50, 50),
                BackgroundColor = -15988609
            };

            AnnotationInfo polylineAnnotation = new AnnotationInfo()
            {
                Type = AnnotationType.Polyline,
                CreatedOn = DateTime.Now,
                Box = new Rectangle((float)250.82807922363281, (float)35.632957458496094, (float)102.70676422119141, (float)12.576337814331055),
                PageNumber = 0,
                PenColor = 65015,
                SvgPath = "M250.8280751173709,48.209295774647885l0.6986854460093896,0l0.6986854460093896, -1.3973708920187793l0.6986854460093896,
                            0l0.6986854460093896,-1.3973708920187793l1.3973708920187793, -0.6986854460093896l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0l2.096056338028169,
                            -1.3973708920187793l3.493427230046948,-1.3973708920187793l0.6986854460093896,-0.6986854460093896l1.3973708920187793,
                            -1.3973708920187793l0.6986854460093896,0l1.3973708920187793,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,
                            -0.6986854460093896l0.6986854460093896,0l0.6986854460093896,0l0,-0.6986854460093896l0.6986854460093896,0l0.6986854460093896,
                            0l1.3973708920187793,0l0,-0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,
                            0l0.6986854460093896,0l2.096056338028169,-0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,
                            0l1.3973708920187793,0l1.3973708920187793,0l1.3973708920187793,0l2.096056338028169,0l5.589483568075117,0l1.3973708920187793,
                            0l2.096056338028169,0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l1.3973708920187793,0l1.3973708920187793,
                            0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0l2.096056338028169,1.3973708920187793l0.6986854460093896,0l0.6986854460093896,
                            0l0,0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0.6986854460093896l1.3973708920187793,0.6986854460093896l0,
                            0.6986854460093896l0.6986854460093896,0l1.3973708920187793,0.6986854460093896l1.3973708920187793,0.6986854460093896l3.493427230046948,
                            0.6986854460093896l1.3973708920187793,0.6986854460093896l2.096056338028169,0.6986854460093896l1.3973708920187793,
                            0.6986854460093896l1.3973708920187793,0l1.3973708920187793,0.6986854460093896l0.6986854460093896,0l0.6986854460093896,
                            0.6986854460093896l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,
                            0l0.6986854460093896,0l1.3973708920187793,0l0.6986854460093896,0l0.6986854460093896,0l1.3973708920187793,
                            0l0.6986854460093896,0l2.7947417840375586,0l0.6986854460093896,0l2.7947417840375586,0l1.3973708920187793,
                            0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,0l0.6986854460093896,
                            0l0.6986854460093896,0l0.6986854460093896,-0.6986854460093896l0.6986854460093896,0"
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
                Box = new Rectangle(200, 250, 50, 0),
                FontSize = 25,
                FontColor = 15988609
            };
            annotations.Add(textAnnotation);
            annotations.Add(pointAnnotation);
            annotations.Add(areaAnnotation);
            annotations.Add(textRedactionAnnotation);
            annotations.Add(resourceRedactionAnnotation);
            annotations.Add(polylineAnnotation);
            annotations.Add(watermarkAnnotation);
            annotations.Add(textFieldAnnotation);
            annotations.Add(strikeoutAnnotation);
            annotations.Add(underlineAnnotation);

            Stream result = annotator.ExportAnnotationsToDocument(cleanPresentation, annotations, DocumentType.Images);

            using (FileStream fileStream = new FileStream("../../Annotated.png", FileMode.Create))
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
