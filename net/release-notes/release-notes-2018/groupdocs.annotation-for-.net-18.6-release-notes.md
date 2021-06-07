---
id: groupdocs-annotation-for-net-18-6-release-notes
url: annotation/net/groupdocs-annotation-for-net-18-6-release-notes
title: GroupDocs.Annotation for .NET 18.6 Release Notes
weight: 7
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 18.6{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 18.6:
*   Implemented using metadata for storing annotations on Slides
*   Implemented support of adding new types of annotations for Diagrams:
    1.  Watermark
    2.  Point
*   Implemented support of adding new types of annotations for Words:
    1.  Polyline
    2.  Watermark
    3.  Point

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-714 | Implemnent support of metadata in Slides | New Feature |
| ANNOTATIONNET-713 | Implement Watermark annotation in Diagrams | New Feature |
| ANNOTATIONNET-706 | Implement adding Point annotation in Diagrams | New Feature |
| ANNOTATIONNET-704 | Implement Polyline annotation for Words | New Feature |
| ANNOTATIONNET-700 | Implement watermark annotation for Words | New Feature |
| ANNOTATIONNET-697 | Implement Point annotation for Words | New Feature |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 18.6. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

1.  Added new types of annotations for Diagrams (Watermark, Point)
    ```csharp
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Reflection;
    using GroupDocs.Annotation.Config;
    using GroupDocs.Annotation.Domain;
    using GroupDocs.Annotation.Handler;
     
     
    namespace AddAnnotations
    {
        public class AddAnnotationsDiagram
        {
            public void Perform()
            {
                AnnotationConfig cfg = new AnnotationConfig();
                cfg.StoragePath = "StorageFolder";
                AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);
                Stream cleanDiagramFile = new FileStream("../../DiagramWithShapeAndText.vsd", FileMode.Open,FileAccess.ReadWrite); 
    Assembly.GetExecutingAssembly().GetManifestResourceStream("AddAnnotations.TestData.");
                List<AnnotationInfo> annotations = new List<AnnotationInfo>();
     
     
                // Area annotation with 2 replies
                AnnotationInfo areaAnnnotation = new AnnotationInfo()
                {
                    CreatedOn = DateTime.Now,
                    Type = AnnotationType.Area,
                    Box = new Rectangle(200, 114.5f, 282.3f, 103.7f),
                };
     
     
                // Polyline annotation
                AnnotationInfo polylineAnnotation = new AnnotationInfo
                {
                    CreatedOn = DateTime.Now,
                    Type = AnnotationType.Polyline,
                    Box = new Rectangle(206.3f, 106.61f, 456.04f, 307.97f),
                    SvgPath = "M436.293427230047,148.06338028169014l0,-0.9870892018779343l-0.9870892018779343,-0.9870892018779343l-1.9741784037558685,-0.9870892018779343l-0.9870892018779343,0l-0.9870892018779343,-0.9870892018779343l-1.9741784037558685,-0.9870892018779343l-0.9870892018779343,0l-1.9741784037558685,-0.9870892018779343l-1.9741784037558685,0l-4.935446009389671,-1.9741784037558685l-1.9741784037558685,0l-1.9741784037558685,-0.9870892018779343l-1.9741784037558685,0l-1.9741784037558685,-0.9870892018779343l-2.961267605633803,0l-2.961267605633803,0l-2.961267605633803,0l-2.961267605633803,0l-2.961267605633803,0l-2.961267605633803,0l-1.9741784037558685,0l-3.948356807511737,0l-2.961267605633803,0l-3.948356807511737,0l-4.935446009389671,0l-3.948356807511737,0.9870892018779343l-4.935446009389671,0.9870892018779343l-6.90962441314554,0l-3.948356807511737,0.9870892018779343l-3.948356807511737,0l-2.961267605633803,1.9741784037558685l-3.948356807511737,0.9870892018779343l-6.90962441314554,1.9741784037558685l-6.90962441314554,0.9870892018779343l-12.832159624413146,2.961267605633803l-6.90962441314554,1.9741784037558685l-5.922535211267606,0.9870892018779343l-5.922535211267606,1.9741784037558685l-5.922535211267606,1.9741784037558685l-5.922535211267606,0.9870892018779343l-4.935446009389671,1.9741784037558685l-5.922535211267606,1.9741784037558685l-5.922535211267606,1.9741784037558685l-4.935446009389671,1.9741784037558685l-5.922535211267606,2.961267605633803l-5.922535211267606,3.948356807511737l-5.922535211267606,3.948356807511737l-4.935446009389671,3.948356807511737l-5.922535211267606,3.948356807511737l-5.922535211267606,3.948356807511737l-3.948356807511737,5.922535211267606l-        3.948356807511737,4.935446009389671l-3.948356807511737,5.922535211267606l-3.948356807511737,6.90962441314554l-3.948356807511737,7.896713615023474l-0.9870892018779343,6.90962441314554l-1.9741784037558685,7.896713615023474l-1.9741784037558685,6.90962441314554l-0.9870892018779343,7.896713615023474l0,12.832159624413146l0,7.896713615023474l0,7.896713615023474l0.9870892018779343,7.896713615023474l1.9741784037558685,5.922535211267606l2.961267605633803,5.922535211267606l0.9870892018779343,5.922535211267606l2.961267605633803,6.90962441314554l3.948356807511737,5.922535211267606l4.935446009389671,4.935446009389671l3.948356807511737,5.922535211267606l3.948356807511737,5.922535211267606l3.948356807511737,5.922535211267606l5.922535211267606,5.922535211267606l5.922535211267606,5.922535211267606l5.922535211267606,5.922535211267606l6.90962441314554,5.922535211267606l7.896713615023474,5.922535211267606l7.896713615023474,5.922535211267606l17.767605633802816,8.883802816901408l11.845070422535212,3.948356807511737l11.845070422535212,4.935446009389671l23.690140845070424,8.883802816901408l41.45774647887324,6.90962441314554l31.586854460093896,3.948356807511737l16.780516431924884,0l16.780516431924884,1.9741784037558685l16.780516431924884,0l16.780516431924884,0l16.780516431924884,0l16.780516431924884,0l16.780516431924884,-1.9741784037558685l14.806338028169014,-1.9741784037558685l14.806338028169014,-1.9741784037558685l12.832159624413146,-1.9741784037558685l10.857981220657276,-2.961267605633803l10.857981220657276,-2.961267605633803l8.883802816901408,-4.935446009389671l8.883802816901408,-4.935446009389671l6.90962441314554,-6.90962441314554l6.90962441314554,-6.90962441314554l8.883802816901408,-16.780516431924884l4.935446009389671,-7.896713615023474l3.948356807511737,-8.883802816901408l4.935446009389671,-7.896713615023474l4.935446009389671,-7.896713615023474l3.948356807511737,-13.81924882629108l1.9741784037558685,-18.754694835680752l0,-7.896713615023474l0,-12.832159624413146l-1.9741784037558685,-15.793427230046948l-1.9741784037558685,-15.793427230046948l-4.935446009389671,-15.793427230046948l-8.883802816901408,-15.793427230046948l-12.832159624413146,-23.690140845070424l-10.857981220657276,-10.857981220657276l-5.922535211267606,-3.948356807511737l-12.832159624413146,-8.883802816901408l-9.870892018779342,-8.883802816901408l-5.922535211267606,-3.948356807511737l-12.832159624413146,-5.922535211267606l-15.793427230046948,-8.883802816901408l-13.81924882629108,-4.935446009389671l-11.845070422535212,-2.961267605633803l-11.845070422535212,-3.948356807511737l-11.845070422535212,-3.948356807511737l-5.922535211267606,-1.9741784037558685l-11.845070422535212,-2.961267605633803l-11.845070422535212,-1.9741784037558685l-5.922535211267606,-0.9870892018779343l-10.857981220657276,-1.9741784037558685l-10.857981220657276,-2.961267605633803l-9.870892018779342,0l-0.9870892018779343,0l-0.9870892018779343,0l-0.9870892018779343,0l-0.9870892018779343,0l0,-0.9870892018779343l1.9741784037558685,0",
                };
     
     
                // Text field annotation
                AnnotationInfo textFieldAnnotation = new AnnotationInfo
                {
                    CreatedOn = DateTime.Now,
                    Type = AnnotationType.TextField,
                    Box = new Rectangle(162.87f, 267.5f, 91.8f, 42.45f),
                    BackgroundColor = -15988609,
                    FieldText = "Annotation Text"
                };
     
     
                // Arrow annotation
                AnnotationInfo arrowAnnotation = new AnnotationInfo
                {
                    Type = AnnotationType.Arrow,
                    Box = new Rectangle(435.77464788732397f, 148.05164319248826f, -66.34389671361504f, 53.07511737089203f)
                };
     
     
                // Resource redaction annotation
                AnnotationInfo resourceRedactionAnnotation = new AnnotationInfo
                {
                    Type = AnnotationType.ResourcesRedaction,
                    Box = new Rectangle(200, 114.5f, 282.3f, 103.7f),
                };
     
                // Distance annotation
                AnnotationInfo distanceAnnnotation = new AnnotationInfo
                {
                    Box = new Rectangle((float)248.73202514648438, (float)287.85653686523438, (float)115.9178466796875, (float)25.143020629882812),
                    CreatedOn = DateTime.Now,
                    Opacity = 0.3,
                    PageNumber = 0,
                    SvgPath = "M248.73201877934272,295.5439436619718 l115.28309859154929,-4.192112676056338",
                    Type = AnnotationType.Distance,
                };
     
                // Point annotation
                AnnotationInfo pointAnnnotation = new AnnotationInfo()
                {
                    Box = new Rectangle(150.32f, 99.22f, 0, 0),
                    CreatedOn = DateTime.Now,
                    PageNumber = 0,
                    Type = AnnotationType.Point,
                };
                 
                // Watermark annotation
                AnnotationInfo watermarkAnnnotation = new AnnotationInfo()
                {
                    Box = new Rectangle(165.41f, 192.24f, 177.8f, 38.29f),
                    CreatedOn = DateTime.Now,
                    FieldText = "Watermark text",
                    FontColor = 16711680,
                    FontFamily = "Microsoft Sans Serif",
                    FontSize = 17,
                    Opacity = 0.3,
                    Type = AnnotationType.Watermark,
                };
                annotations.Add(areaAnnnotation);
                annotations.Add(polylineAnnotation);
                annotations.Add(textFieldAnnotation);
                annotations.Add(arrowAnnotation);
                annotations.Add(resourceRedactionAnnotation);
                annotations.Add(distanceAnnnotation);
                annotations.Add(pointAnnnotation);
                annotations.Add(watermarkAnnnotation);
     
                // Add annotation to the document
                Stream result = annotator.ExportAnnotationsToDocument(cleanDiagramFile, annotations);
     
     
                // Save result stream to file.
                using (FileStream fileStream = new FileStream("../../Annotated.vsdx", FileMode.Create))
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
    
2.  Added new types of annotations for Words (Polyline, Watermark, Point)
    
    ```csharp
    using System.Collections.Generic;
    using System.IO;
    using System.Reflection;
    using GroupDocs.Annotation;
    using GroupDocs.Annotation.Config;
    using GroupDocs.Annotation.Domain;
    using GroupDocs.Annotation.Handler;
     
    namespace AddAnnotationsWords
    {
        class Program
        {
            static void Main(string[] args)
            {
                AnnotationConfig cfg = new AnnotationConfig();
                cfg.StoragePath = "StorageFolder";
                AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);
     
     
                new License().SetLicense("proper_path_to_license");
     
     
                Stream cleanDoc = new FileStream("../../AddAnnotationsWords.TestData.Clear.docx", FileMode.Open, FileAccess.ReadWrite);
                List<AnnotationInfo> annotations = new List<AnnotationInfo>();
                 
                //init possible types of annotations
                AnnotationInfo textAnnotation = new AnnotationInfo
                {
                    PageNumber = 0,
                    SvgPath = "[{\"x\":186.698,\"y\":706.196},{\"x\":318.41201,\"y\":706.196},{\"x\":186.698,\"y\":697.196},{\"x\":318.41201,\"y\":697.196}]",
                    Type = AnnotationType.Text
                };
                 
                AnnotationInfo areaAnnnotation = new AnnotationInfo
                {
                    BackgroundColor = 11111111,
                    Box = new Rectangle(87.9f, 276.5f, 435.7f, 87f),
                    PageNumber = 0,
                    Type = AnnotationType.Area
                };
                 
                AnnotationInfo strikeoutAnnotation = new AnnotationInfo
                {
                    Box = new Rectangle(87.9f, 276.5f, 435.7f, 87f),
                    PageNumber = 0,
                    PenColor = 1201033,
                    SvgPath = "[{\"x\":208.392,\"y\":313.088},{\"x\":519.659,\"y\":313.088},{\"x\":208.392,\"y\":304.088},{\"x\":519.659,\"y\":304.088}]",
                    Type = AnnotationType.TextStrikeout
                };
                 
                AnnotationInfo textFieldAnnotation = new AnnotationInfo
                {
                    FieldText = "text in the box",
                    FontFamily = "Arial",
                    FontSize = 10,
                    Box = new Rectangle(92f, 73f, 106f, 45f),
                    PageNumber = 1,
                    Type = AnnotationType.TextField,
                };
                 
                AnnotationInfo textReplacementAnnotation = new AnnotationInfo
                {
                    FieldText = " \"REPLACED TEXT\" ",
                    FontSize = 10,
                    SvgPath = "[{\"x\":251.224,\"y\":637.20401},{\"x\":327.89,\"y\":637.20401},{\"x\":251.224,\"y\":628.20401},{\"x\":327.89,\"y\":628.20401}]",
                    PageNumber = 0,
                    Type = AnnotationType.TextReplacement,
                };
                AnnotationInfo arrowAnnotation = new AnnotationInfo
                {
                    Box = new Rectangle(479f, 218f, -261f, -89f),
                    PageNumber = 0,
                    Type = AnnotationType.Arrow,
                };
     
                AnnotationInfo textRedactionAnnotation = new AnnotationInfo
                {
                    PageNumber = 1,
                    SvgPath = "[{\"x\":72,\"y\":676.07},{\"x\":196.427,\"y\":676.074},{\"x\":72,\"y\":662.674},{\"x\":196.427,\"y\":662.674}]",
                    Type = AnnotationType.TextRedaction,
                };
     
                AnnotationInfo resourceRedactionAnnotation = new AnnotationInfo
                {
                    Box = new Rectangle(69f, 337f, 449f, 118f),
                    PageNumber = 1,
                    Type = AnnotationType.ResourcesRedaction,
                };
     
                AnnotationInfo underlineAnnotation = new AnnotationInfo
                {
                    PageNumber = 1,
                    SvgPath = "[{\"x\":415.17499,\"y\":628.874},{\"x\":511.85101,\"y\":628.874},{\"x\":415.17499,\"y\":619.874},{\"x\":511.85101,\"y\":619.874}]",
                    Type = AnnotationType.TextUnderline
                };
     
                AnnotationInfo distanceAnnnotation = new AnnotationInfo
                {
                    Box = new Rectangle((float)248.73202514648438, (float)287.85653686523438, (float)115.9178466796875, (float)25.143020629882812),
                    Opacity = 0.3,
                    PageNumber = 0,
                    SvgPath = "M248.73201877934272,295.5439436619718 l115.28309859154929,-4.192112676056338",
                    Type = AnnotationType.Distance,
                };
     
                AnnotationInfo pointAnnnotation = new AnnotationInfo
                {
                    Box = new Rectangle(185.9f, 371.92f, 0, 0),
                    PageNumber = 0,
                    Type = AnnotationType.Point
                };
     
                AnnotationInfo watermarkAnnotation = new AnnotationInfo
                {
                    FieldText = "watermark text",
                    FontFamily = "Microsoft Sans Serif",
                    FontSize = 17,
                    Box = new Rectangle(195.225f, 216.464f, 230.73f, 58.18f),
                    PageNumber = 0,
                    Type = AnnotationType.Watermark,
                    FontColor = 16711680
                };
                 
                AnnotationInfo polylineAnnotation = new AnnotationInfo
                {
                    PageNumber = 0,
                    Type = AnnotationType.Polyline,
                    Box = new Rectangle(288.760559f, 533.7042f, 216.929581f, 171.676056f),
                    SvgPath = "M504.9718309859155,678.0845070422536l-0.7183098591549296,0l-0.7183098591549296,0l-0.7183098591549296,0.7183098591549296l-0.7183098591549296,0.7183098591549296l-1.4366197183098592,0.7183098591549296l-2.154929577464789,2.154929577464789l-2.8732394366197185,0.7183098591549296l-5.028169014084507,2.154929577464789l-6.464788732394367,3.591549295774648l-10.774647887323944,3.591549295774648l-10.056338028169014,2.154929577464789l-9.338028169014084,2.154929577464789l-8.619718309859156,2.154929577464789l-9.338028169014084,3.591549295774648l-7.183098591549296,0l-7.183098591549296,0.7183098591549296l-5.028169014084507,0.7183098591549296l-5.746478873239437,1.4366197183098592l-5.746478873239437,0l-8.619718309859156,0l-12.211267605633804,0l-6.464788732394367,0l-8.619718309859156,-1.4366197183098592l-7.901408450704226,-3.591549295774648l-10.774647887323944,-5.746478873239437l-8.619718309859156,-5.028169014084507l-9.338028169014084,-5.746478873239437l-12.211267605633804,-9.338028169014084l-10.056338028169014,-10.056338028169014l-5.746478873239437,-7.901408450704226l-           6.464788732394367,-12.211267605633804l-2.154929577464789,-3.591549295774648l-5.028169014084507,-13.647887323943662l-2.154929577464789,-7.901408450704226l0,-7.183098591549296l0,-9.338028169014084l0,-5.746478873239437l2.8732394366197185,-7.901408450704226l5.028169014084507,-5.746478873239437l6.464788732394367,-7.183098591549296l10.774647887323944,-7.901408450704226l10.774647887323944,-6.464788732394367l15.084507042253522,-6.464788732394367l14.366197183098592,-6.464788732394367l22.267605633802816,-7.183098591549296l13.647887323943662,-3.591549295774648l14.366197183098592,-3.591549295774648l16.52112676056338,-0.7183098591549296l16.52112676056338,0l15.084507042253522,0l10.774647887323944,0l7.183098591549296,2.154929577464789l4.309859154929578,2.154929577464789l5.028169014084507,2.8732394366197185l3.591549295774648,2.154929577464789l3.591549295774648,2.8732394366197185l6.464788732394367,6.464788732394367l2.8732394366197185,4.309859154929578l2.154929577464789,2.154929577464789l2.154929577464789,4.309859154929578l1.4366197183098592,2.8732394366197185l2.154929577464789,5.028169014084507l0.7183098591549296,3.591549295774648l0.7183098591549296,5.028169014084507l0,5.028169014084507l0,4.309859154929578l0,7.183098591549296l-0.7183098591549296,2.8732394366197185l-3.591549295774648,6.464788732394367l-3.591549295774648,6.464788732394367l-4.309859154929578,5.028169014084507l-5.028169014084507,5.028169014084507l-7.183098591549296,4.309859154929578l-7.183098591549296,4.309859154929578l-10.774647887323944,6.464788732394367l-9.338028169014084,4.309859154929578l-9.338028169014084,4.309859154929578l-10.056338028169014,2.8732394366197185l-7.901408450704226,2.8732394366197185l-10.774647887323944,1.4366197183098592l-5.028169014084507,0.7183098591549296l-3.591549295774648,0l-2.8732394366197185,0l-3.591549295774648,0l-5.028169014084507,0l-5.746478873239437,0l-7.183098591549296,-1.4366197183098592l-5.746478873239437,-1.4366197183098592l-6.464788732394367,-2.8732394366197185l-4.309859154929578,-1.4366197183098592l-2.154929577464789,-1.4366197183098592l-1.4366197183098592,-0.7183098591549296l-1.4366197183098592,-0.7183098591549296l-0.7183098591549296,-0.7183098591549296l-1.4366197183098592,-1.4366197183098592l0,-0.7183098591549296l-1.4366197183098592,-0.7183098591549296l0,-1.4366197183098592l-0.7183098591549296,-0.7183098591549296l0,-0.7183098591549296",
                };
                 
                annotations.Add(textAnnotation);
                annotations.Add(areaAnnnotation);
                annotations.Add(strikeoutAnnotation);
                annotations.Add(textFieldAnnotation);
                annotations.Add(textReplacementAnnotation);
                annotations.Add(arrowAnnotation);
                annotations.Add(textRedactionAnnotation);
                annotations.Add(resourceRedactionAnnotation);
                annotations.Add(underlineAnnotation);
                annotations.Add(distanceAnnnotation);
                annotations.Add(pointAnnnotation);
                annotations.Add(watermarkAnnotation);
                annotations.Add(polylineAnnotation);
                // Add annotation to the document
                Stream result = annotator.ExportAnnotationsToDocument(cleanDoc, annotations, DocumentType.Words);
     
                // Save result stream to file.
                using(FileStream fileStream = new FileStream("../../Annotated.docx", FileMode.Create))
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
