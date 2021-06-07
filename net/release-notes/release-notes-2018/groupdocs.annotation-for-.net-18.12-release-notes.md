---
id: groupdocs-annotation-for-net-18-12-release-notes
url: annotation/net/groupdocs-annotation-for-net-18-12-release-notes
title: GroupDocs.Annotation for .NET 18.12 Release Notes
weight: 1
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 18.12{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 18.12:
*   Implemented export only pages that contains annotations
*   Implemented export document with annotations of specific type
*   Export specific range of pages of document
*   Add possibility to retrieve pages without annotations
*   Ensured and updated GroupDocs.Annotation code is thread-safe.
*   Fixed when GetDocumentInfo method in trial mode throws exception
*   Add text replacement annotation for grouped shapes for Slides.
*   Fixed issue with trowing NotSupportedException exception when pass password parameter for Images.
*   Fixed issue when apply annotation to empty document in Cells.

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-812 | Implement export only pages that contains annotations | Feature |
| ANNOTATIONNET-813 | Implement Export document with specific annotation type | Feature |
| ANNOTATIONNET-814  | Export specific pages range of document | Feature |
| ANNOTATIONNET-815 | Add possibility to retrieve pages without annotations | Feature |
| ANNOTATIONNET-806 | Ensured and updated GroupDocs.Annotation code is thread-safe. | Improvement |
| ANNOTATIONNET-811 | Add text replacement for grouped shapes. | Improvement |
| ANNOTATIONNET-819  | AnnotationImageHandler.GetDocumentInfo method in trial mode throws exception | Bug |
| ANNOTATIONNET-821  | Bug during apply annotation to empty document in Cells. | Bug |
| ANNOTATIONNET-826  | NotSupportedException exception when pass password parameter for Images. | Bug |

## Public API and Backward Incompatible Change

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 18.12. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

1.  **Export page range**.  
    To export specific pages  you should just to setup *ExportOptions *class, and then export as before.
    
    ```csharp
    ExportOptions options = new ExportOptions
    {
       FirstPage = 5,
       LastPage = 8
    };
    ```
    
    Result: will be exported document pages started from page 6 and ending page 9.
    
    ```csharp
    ExportOptions options = new ExportOptions
    {
       FirstPage = 4,
       LastPage = 4
    };
    ```
    
    Result: document will contain only one page with index 5.
    
    Note: there will be no effect if:
    
    *   FirstPage > LastPage
        
    *   If FirstPage or / and LastPage < 0
        
    *   If LastPage > document pages number
        
    
2.  ****Export only pages with annotations****.  
    To export only pages that contains annotations you should specify *AnnotatedPages = true *of *ExportOptions *class.
    
    ```csharp
    ExportOptions options = new ExportOptions
    {
        AnnotatedPages = true
    };
    ```
    
    Result: document that contains only annotated pages.
    
    ```csharp
    ExportOptions options = new ExportOptions
    {
      FirstPage = 5,
      LastPage = 8,
      AnnotatedPages = true
    };
    ```
    
    Result: A document that contains only annotated pages inside this page range. If there are not annotated pages, then the document will contains only pages from a specific range.
    
3.  ******Export annotations of specific types******.
    
    ```csharp
    List<AnnotationType> typesToExport = new List<AnnotationType>();
    typesToExport.Add(AnnotationType.Area);
    typesToExport.Add(AnnotationType.Polyline);
     
    ExportOptions options = new ExportOptions
    {
       AnnotationTypes = typesToExport
    };
    ```
    
    Result: A document that contains only Area and Polyline annotations.
    
    ```csharp
    List<AnnotationType> typesToExport = new List<AnnotationType>();
    typesToExport.Add(AnnotationType.Area);
     
    ExportOptions options = new ExportOptions
    {
      AnnotationTypes = typesToExport,
      AnnotatedPages = true
    };
    ```
    
    Result: A document that contains only annotated pages with Area annotations.
    
    ```csharp
    List<AnnotationType> typesToExport = new List<AnnotationType>();
    typesToExport.Add(AnnotationType.Area);
     
    ExportOptions options = new ExportOptions
    {
       FirstPage = 5,
       LastPage = 8,
       AnnotationTypes = typesToExport,
       AnnotatedPages = true
    };
    ```
    
    Result: A document that contains only annotated pages with Area annotations inside range from 5th to 8th page. If no Area annotation inside this range, then document just contains pages from 5 to 8.
