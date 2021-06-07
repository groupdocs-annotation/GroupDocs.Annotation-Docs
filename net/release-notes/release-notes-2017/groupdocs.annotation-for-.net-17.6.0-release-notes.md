---
id: groupdocs-annotation-for-net-17-6-0-release-notes
url: annotation/net/groupdocs-annotation-for-net-17-6-0-release-notes
title: GroupDocs.Annotation for .NET 17.6.0 Release Notes
weight: 6
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 17.6.0{{< /alert >}}

## Major Features

Below the list of  new features and fixed bugs in this regular monthly release of GroupDocs.Annotation for .NET. The most notable are:

*   Added support of annotation Diagrams documents (vsd, vss)  
    1.  Arrow annotation
    2.  Area annotation
    3.  ResourceRedaction annotation
    4.  Polyline annotation
    5.  TextField annotation
*   Implement proper error handling when user try to invoke GetDocumentInfo method for images documents
*   Updated and improved library obfuscation

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-417 | Implement Polyline annotation with Diagram documents | New Feature |
| ANNOTATIONNET-416 | Implement Arrow annotation for Diagram documents | New Feature |
| ANNOTATIONNET-410 | Implement Area annotation for Diagrams | New Feature |
| ANNOTATIONNET-406 | Add option to process CAD documents as PDF | Improvement |
| ANNOTATIONNET-405 | Implement GetPages method for Email documents processing from streams | Improvement |
| ANNOTATIONNET-401 | Implement proper error handling when user try to invoke GetDocumentInfo method for images documents | Improvement |
| ANNOTATIONNET-395 | Internal Exception in annotator.GetDocumentInfo() Method | Bug |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 17.6.0. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

###  How to add different Annotations to Diagram Documents

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
                SvgPath = "M436.293427230047,148.06338028169014l0,-0.9870892018779343l-0.9870892018779343,-0.9870892018779343l-1.9741784037558685,-0.9870892018779343l-0.9870892018779343,0l-0.9870892018779343,-0.9870892018779343l-1.9741784037558685,-0.9870892018779343l-0.9870892018779343,0l-1.9741784037558685,-0.9870892018779343l-1.9741784037558685,0l-4.935446009389671,-1.9741784037558685l-1.9741784037558685,0l-1.9741784037558685,-0.9870892018779343l-1.9741784037558685,0l-1.9741784037558685,-0.9870892018779343l-2.961267605633803,0l-2.961267605633803,0l-2.961267605633803,0l-2.961267605633803,0l-2.961267605633803,0l-2.961267605633803,0l-1.9741784037558685,0l-3.948356807511737,0l-2.961267605633803,0l-3.948356807511737,0l-4.935446009389671,0l-3.948356807511737,0.9870892018779343l-4.935446009389671,0.9870892018779343l-6.90962441314554,0l-3.948356807511737,0.9870892018779343l-3.948356807511737,0l-2.961267605633803,1.9741784037558685l-3.948356807511737,0.9870892018779343l-6.90962441314554,1.9741784037558685l-6.90962441314554,0.9870892018779343l-12.832159624413146,2.961267605633803l-6.90962441314554,1.9741784037558685l-5.922535211267606,0.9870892018779343l-5.922535211267606,1.9741784037558685l-5.922535211267606,1.9741784037558685l-5.922535211267606,0.9870892018779343l-4.935446009389671,1.9741784037558685l-5.922535211267606,1.9741784037558685l-5.922535211267606,1.9741784037558685l-4.935446009389671,1.9741784037558685l-5.922535211267606,2.961267605633803l-5.922535211267606,3.948356807511737l-5.922535211267606,3.948356807511737l-4.935446009389671,3.948356807511737l-5.922535211267606,3.948356807511737l-5.922535211267606,3.948356807511737l-3.948356807511737,5.922535211267606l-		3.948356807511737,4.935446009389671l-3.948356807511737,5.922535211267606l-3.948356807511737,6.90962441314554l-3.948356807511737,7.896713615023474l-0.9870892018779343,6.90962441314554l-1.9741784037558685,7.896713615023474l-1.9741784037558685,6.90962441314554l-0.9870892018779343,7.896713615023474l0,12.832159624413146l0,7.896713615023474l0,7.896713615023474l0.9870892018779343,7.896713615023474l1.9741784037558685,5.922535211267606l2.961267605633803,5.922535211267606l0.9870892018779343,5.922535211267606l2.961267605633803,6.90962441314554l3.948356807511737,5.922535211267606l4.935446009389671,4.935446009389671l3.948356807511737,5.922535211267606l3.948356807511737,5.922535211267606l3.948356807511737,5.922535211267606l5.922535211267606,5.922535211267606l5.922535211267606,5.922535211267606l5.922535211267606,5.922535211267606l6.90962441314554,5.922535211267606l7.896713615023474,5.922535211267606l7.896713615023474,5.922535211267606l17.767605633802816,8.883802816901408l11.845070422535212,3.948356807511737l11.845070422535212,4.935446009389671l23.690140845070424,8.883802816901408l41.45774647887324,6.90962441314554l31.586854460093896,3.948356807511737l16.780516431924884,0l16.780516431924884,1.9741784037558685l16.780516431924884,0l16.780516431924884,0l16.780516431924884,0l16.780516431924884,0l16.780516431924884,-1.9741784037558685l14.806338028169014,-1.9741784037558685l14.806338028169014,-1.9741784037558685l12.832159624413146,-1.9741784037558685l10.857981220657276,-2.961267605633803l10.857981220657276,-2.961267605633803l8.883802816901408,-4.935446009389671l8.883802816901408,-4.935446009389671l6.90962441314554,-6.90962441314554l6.90962441314554,-6.90962441314554l8.883802816901408,-16.780516431924884l4.935446009389671,-7.896713615023474l3.948356807511737,-8.883802816901408l4.935446009389671,-7.896713615023474l4.935446009389671,-7.896713615023474l3.948356807511737,-13.81924882629108l1.9741784037558685,-18.754694835680752l0,-7.896713615023474l0,-12.832159624413146l-1.9741784037558685,-15.793427230046948l-1.9741784037558685,-15.793427230046948l-4.935446009389671,-15.793427230046948l-8.883802816901408,-15.793427230046948l-12.832159624413146,-23.690140845070424l-10.857981220657276,-10.857981220657276l-5.922535211267606,-3.948356807511737l-12.832159624413146,-8.883802816901408l-9.870892018779342,-8.883802816901408l-5.922535211267606,-3.948356807511737l-12.832159624413146,-5.922535211267606l-15.793427230046948,-8.883802816901408l-13.81924882629108,-4.935446009389671l-11.845070422535212,-2.961267605633803l-11.845070422535212,-3.948356807511737l-11.845070422535212,-3.948356807511737l-5.922535211267606,-1.9741784037558685l-11.845070422535212,-2.961267605633803l-11.845070422535212,-1.9741784037558685l-5.922535211267606,-0.9870892018779343l-10.857981220657276,-1.9741784037558685l-10.857981220657276,-2.961267605633803l-9.870892018779342,0l-0.9870892018779343,0l-0.9870892018779343,0l-0.9870892018779343,0l-0.9870892018779343,0l0,-0.9870892018779343l1.9741784037558685,0",
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


            annotations.Add(areaAnnnotation);
            annotations.Add(polylineAnnotation);
            annotations.Add(textFieldAnnotation);
            annotations.Add(arrowAnnotation);
            annotations.Add(resourceRedactionAnnotation);

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
