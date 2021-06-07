---
id: groupdocs-annotation-for-net-20-4-release-notes
url: annotation/net/groupdocs-annotation-for-net-20-4-release-notes
title: GroupDocs.Annotation for .NET 20.4 Release Notes
weight: 100
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 20.4{{< /alert >}}

## Major Features

Below the list of most notable changes in  release of GroupDocs.Annotation for .NET 20.4:

*   Added new feature for managing different versions of annotated documents (supported formats: Words, PDF, PowerPoint and Open Document format presentations, Excel and Open Document format spreadsheets)
*   Added advanced rendering options for show\\hide replies
*   Added to new API getting pages image size
*   Fixed issue with throwing exception for encrypted Excel spreadsheets
*   Fixed cleanup replies for PowerPoint presentations
*   Fixed issue with closed stream

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Type |
| --- | --- | --- |
| ANNOTATIONNET-816 | Managing different versions of annotated file | Feature |
| ANNOTATIONNET-1320 | Pages image size | Improvement |
| ANNOTATIONNET-1318 | Document advanced rendering modes and options support | Improvement |
| ANNOTATIONNET-1296 | Cannot access a closed Stream | Bug |
| ANNOTATIONNET-1284 | Encrypted Excel spreadsheet file throws exception | Bug |
| ANNOTATIONNET-1321 | CleanUp method for PowerPoint presentation does not remove replies | Bug |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 20.4. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

## 1\. Versions of Annotated files

Every Time you Save file using Annotator.Save() method - you implicitly create a new version of the annotated file. Versions List stores not document, it keeps annotations that you add, remove, and change. So you can easy swap between different changes made with GroupDocs.Annotation. And of course you can set your version names. More information about how it works you can find in child Pages

By default, they are created using unique GUID keys. Next, each aspect of using versions will be considered. The API execution logic has not changed, so you do not need to change your code to use it as before. By default, the latest version is loaded without your fate (that is, you will not notice the difference with previous releases). 

### Backward Compatibility

The update is fully compatible with previous and next updates (The latest saved version will be used), however, using versions on previous versions is not possible and the list of versions in this document will not be changed. And If you update file from 20.4+ using 20.2 and lower few times, after loading this document on 20.4+ only last changes will be added as new version.

### Add Version with custom name

If you want to swap between versions easily you might need to have ability to set custom versions names.

Here the code that demonstrates how to save version with custom name:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
   annotator.Update(new AreaAnnotation{ Box = new Rectangle(100, 100, 100, 100) });
   annotator.Save("result.pdf", new SaveOptions { Version = "CUSTOM_VERSION" });
}
```

{{< alert style="info" >}}Version Property type is object, so it support any type, and you can use any variable as version variable{{< /alert >}}

### Get List of All version keys on a document

If you don't know what versions were added earlier or want to know versions count
Here the code that demonstrates how to get list of versions keys:

```csharp
using (Annotator annotator = new Annotator("result.pdf")) { 
      List<object> versionKeys = annotator.GetVersionsList();
}
```

{{< alert style="info" >}}Annotator.GetVersionList() returns list of objects because it supports any type of key. But if you used some specified keys as string - you can convert it.{{< /alert >}}

### Get List of Annotations using version key

If you need to get List of Annotations you can use Annotator.GetVersion() method
Here code that demonstrates how to get list of annotations from individual version

```csharp
using (Annotator annotator = new Annotator("result.pdf"))
{
    List<AnnotationBase> annotations = annotator.GetVersion("CUSTOM_VERSION");
}
```

{{< alert style="info" >}}GetVersion method supports any type, and you can use any variable as version variable.{{< /alert >}}

### Load Document of custom Version

Using LoadOptions.Version you can load previous versions of annotated document.
Here the code that demonstrates how load version using version name:

```csharp
using (Annotator annotator = new Annotator($"result.{ext}", new LoadOptions { Version = "CUSTOM_VERSION" }))
{
  annotator.Save("result_loaded.pdf");
}
```

{{< alert style="info" >}}Version Property type is object, so it support any type, and you can use any variable as a version.{{< /alert >}}

## 2\. Added RenderComments Property to PreviewOptions

If you need not to generate comments on image preview you may use *RenderComments* property

{{< alert style="info" >}}This feature is only supported for Word processing documents.{{< /alert >}}

Default value is *true*. If it is not needed to display replies and comments at the page preview - set *RenderComments* property to *false* (replies and comments still will be stored inside document).  
Please notice, that *RenderComments* value will impact any document comments (doesn't matter if they were added by GroupDocs.Annotation or  some other application).
Here the code that demonstrates how display image preview without comments:

```csharp
Annotator annotator = new Annotator(File.OpenRead(MakeStoragePath(inputPath)));
           PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
           {
               var pagePath = MakeStoragePath(inputPath.Replace("input.doc", $"result{pageNumber}.png"));
               return File.Create(pagePath);
           });
previewOptions.PreviewFormat = PreviewFormats.PNG;
previewOptions.RenderComments = false;
annotator.Document.GeneratePreview(previewOptions);
```

## 3\. Add PagesInfo property to IDocumentInfo

*PagesInfo* represents list of *PageInfo* objects which store information about each page.

Now *PageInfo* have two properties - *Width* and *Height* in pixels. This properties works with all formats except Email And Html that doesn't have height and width so the won't store them and will be empty. All pages width and height will be same in all formats except Cells, so you can use size of first element as size of all document.

Here code that demonstrates how to get Document width and Height:

```csharp
Annotator annotator = new Annotator("input.docx");
IDocumentInfo info = annotator.Document.GetDocumentInfo();
int width = info.PagesInfo[0].Width;
int height = info.PagesInfo[0].Height;
```
