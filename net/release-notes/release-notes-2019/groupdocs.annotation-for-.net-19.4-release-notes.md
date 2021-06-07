---
id: groupdocs-annotation-for-net-19-4-release-notes
url: annotation/net/groupdocs-annotation-for-net-19-4-release-notes
title: GroupDocs.Annotation for .NET 19.4 Release Notes
weight: 7
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 19.4{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 19.4:

*   Implemented link annotation in Pdf, Slides and Words formats
*   Added ability to convert protected documents in GetPdfFile method
*   Fixed problem that documents with password can’t be converted
*   Fixed issue with GetPdfFile returns damaged file
*   Fixed empty GUID exception in Cells
*   Fixed problem with removing annotation from Cells
*   Fixed TIFF image stream not disposed during import annotations

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-941 | Implement Link annotation for Slides | Feature |
| ANNOTATIONNET-942 | Implement Link annotation for PDF | Feature |
| ANNOTATIONNET-943 | Implement Link annotation for Words | Feature |
| ANNOTATIONNET-964 | GetPdfFile method doesn't implement converting documents with password | Improvement |
| ANNOTATIONNET-950 | Remove annotations fails with Cells document | Bug |
| ANNOTATIONNET-952 | Documents with password are not converted to PDF | Bug |
| ANNOTATIONNET-963 | GetPdfFile method returns broken file | Bug |
| ANNOTATIONNET-965 | ImportAnnotations method doesn't close source stream for Tiff files | Bug |

## Public API and Backward Incompatible Change

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 19.4. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

1.  Adding Link annotation.  
    Minimal set of fields for Link Annotation. This type of annotation supported for Slides, Words and PDF documents
    
    ```csharp
    AnnotationInfo link= new AnnotationInfo()
    {
       Box = new Rectangle(173.2986, 154.3131, 142.5, 9),
       //URL
       FieldText = "https://www.google.com",
       SvgPath = "[{"x":173.2986,"y":687.5769},{"x":315.79859999999996,"y":687.5769},{"x":173.2986,"y":678.5769},{"x":315.79859999999996,"y":678.5769}]"
       Type = AnnotationType.Link;
    };
    ```  
    
2.  GetPdfFile method can process documents with password.  
    If you need to process document protected with password you should pass extra parameter for GetPdfFile method
    
    ```csharp
    Stream convertedDocument = annotator.GetPdfFile(protectedDocument, "123password123");
    ```
