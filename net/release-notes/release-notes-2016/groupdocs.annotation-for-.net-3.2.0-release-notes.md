---
id: groupdocs-annotation-for-net-3-2-0-release-notes
url: annotation/net/groupdocs-annotation-for-net-3-2-0-release-notes
title: GroupDocs.Annotation for .NET 3.2.0 Release Notes
weight: 5
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 3.2.0{{< /alert >}}

## Major Features

Below the list of improvements fixes and new features in this regular monthly release of GroupDocs.Annotation for .NET. The most notable are:

*   Implement annotations import from Word documents
*   Implement  auto-import annotations when opening PDF documents
*   Add native Word annotations after export to Word documents different types of annotations
*   Fix users permission for Delete annotations

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Category |
| --- | --- | --- |
| ANNOTATIONNET-249 | Import TextField annotation from Words Documents | New Feature |
| ANNOTATIONNET-236 | Implement TextRedaction annotation import from Word | New Feature |
| ANNOTATIONNET-244 | Implement Shape annotations import from Word | New Feature |
| ANNOTATIONNET-237 | Implement TextStrikeout annotation import from Word | New Feature |
| ANNOTATIONNET-238 | Implement Underline annotation import from Word | New Feature |
| ANNOTATIONNET-235 | Implement Area annotation import from Word | New Feature |
| ANNOTATIONNET-234 | Implement Text annotation import from Word | New Feature |
| ANNOTATIONNET-230 | Add native Word annotations after export Word documents to Text Replacement annotation | New Feature |
| ANNOTATIONNET-224 | Add native Word annotations after export Word documents | New Feature |
| ANNOTATIONNET-228 | Add native Word annotations after export Word documents to Strikeout annotation | New Feature |
| ANNOTATIONNET-241 | Implement option for ability to auto-import annotations when opening PDF documents | Improvement |
| ANNOTATIONNET-250 | Fix users permission for Delete annotations | Bug |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 3.2.0. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

#### Import and Export Annotations from Words document



```csharp
            AnnotationConfig cfg = new AnnotationConfig();
            cfg.StoragePath = "TestData";

            AnnotationImageHandler annotator = new AnnotationImageHandler(cfg);
            if (!Directory.Exists(cfg.StoragePath))
            {
                Directory.CreateDirectory(cfg.StoragePath);
            }

            new License().SetLicense("path_to_proper_license");


            //importing annotations from Words document
            Stream stream = new FileStream("ImportAnnotationsWord.TestData.Annotated.docx", FileMode.Open, FileAccess.ReadWrite);

            AnnotationInfo[] annotations = annotator.ImportAnnotations(stream, DocumentType.Words);


            //export imported annotation to another document (just for check)
            Stream clearDocument = new FileStream("../../AddAnnotationsWords.TestData.Clear.docx", FileMode.Open, FileAccess.ReadWrite);
            Stream output = annotator.ExportAnnotationsToDocument(clearDocument, annotations.ToList(), DocumentType.Words);


            //save results after export
            using (FileStream fileStream = new FileStream("../../Annotated.docx", FileMode.Create))
            {
                byte[] buffer = new byte[output.Length];
                output.Seek(0L, SeekOrigin.Begin);
                output.Read(buffer, 0, buffer.Length);
                fileStream.Write(buffer, 0, buffer.Length);
                fileStream.Close();
            }


```
