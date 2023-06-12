---
id: generate-document-pages-preview
url: annotation/net/generate-document-pages-preview
title: Generate document page preview
weight: 3
description: "The page describes how to generate PDF, Word, Excel, PowerPoint documents thumbnails and preview document pages using GroupDocs.Annotation for .NET API."
keywords: Preview document pages, Document pages as PNG, document pages as JPG, Document preview
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to generate document pages preview
        description: Learn how to generate document pages preview step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: PreviewOptions class declaration
          text: Create an instance of PreviewOptions class.
        - name: Specify ptrview options
          text: In the PreviewOptions class constructor, pass the path to the page.
        - name: Property preview
          text: Specify preview format and page numbers
        - name: Generate preview
          text: Call the .GeneratePreview() method and pass the class name PreviewOptions to it
toc: True
---

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/net) allows you to generate document page previews. To do this, call the [GeneratePreview](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/document/methods/generatepreview) method of the [Document](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/properties/document) class. 

Use the [PreviewOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions) class to manage the preview generation process: specify desired page numbers, image format, etc.

To generate a document preview, follow these steps:
1.  Create an instance of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the source document path as a parameter. The [Document](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/properties/document) property of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class provides access to source document and implements [GeneratePreview](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/document/methods/generatepreview) method.
3.   Instantiate the [PreviewOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions) class. Follow these steps:
    a.   for each page, delegate stream creation (see the `CreatePageStream` event handler); 
    b.   specify the image preview format - PNG / JPG / BMP,
    c.   specify page numbers to process;
    d.   set the custom size of preview images (if needed).  
{{< alert style="info" >}} Stream created by the [CreatePageStream](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/createpagestream) delegate are disposed automatically once after generation of preview image. To implement the custom image preview stream disposing, you have to specify an additional argument [ReleasePageStream](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/releasepagestream) to clean up resources.
{{< /alert >}}       
4.  Call the [GeneratePreview](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/document/methods/generatepreview) method of the [Annotator.Document](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/properties/document) class. Specify [PreviewOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions).

    
The [PreviewOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions) class main properties are as follows:
*   [CreatePageStream](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/createpagestream) is a delegate which defines the method to create output page preview stream.
*   [ReleasePageStream](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/releasepagestream) is a delegate which defines the method to remove output page preview stream. Use it for advanced control for resources handling.
*   [Width](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/width) specifies the preview image width.
*   [Height](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/height) specifies the preview image height.
*   [PageNumbers](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/pagenumbers) - Page numbers that will be previewed;
*   [PreviewFormat](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/previewformat) gets or sets the preview image format. Use the BMP format should be used for the best image quality. Use the JPG format in case of strict requirements to image size, but with lower quality than BMP. By default GroupDocs.Annotation uses the PNG format which is a golden mean between image quality and size.
*   [RenderComments](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/rendercomments) is an option to show or hide comments. By default it is `true`. Set it to `false` if you do not need to show comments. This property affects only on WordProcessing documents. The `RenderComments` value impacts any document comments.
*   [RenderAnnotations](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/renderannotations) is an option to show or hide annotations.By default it is `true`. Set it to `false` if you do not need to show annotations.
*   [WorksheetColumns](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/worksheetcolumns) is a list of the [WorksheetColumnsRange](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/worksheetcolumnsrange) objects that indicates which columns to generate on specified worksheet.

The following code snippet demonstrates how to generate document previews.

## Get document page previews 

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"D:/result_{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
    annotator.Document.GeneratePreview(previewOptions);
}
```
{{< /tab >}}
{{< /tabs >}}

## Set specific size for preview images

You can set a specific size for preview images. For example, you can create small-sized thumbnails and full-sized previews.

The following code snippet shows how to set specific size for preview images:

{{< tabs "example2">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"D:/result_{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
	previewOptions.Height = 100;
    previewOptions.Width = 80;
    annotator.Document.GeneratePreview(previewOptions);   
}

```
{{< /tab >}}
{{< /tabs >}}

## Get page previews with manual resource cleaning

By default, GroupDocs.Annotation deletes the image stream immediately after creating and rendering the document page. If necessary, you can implement a custom method to perform this operation.

{{< tabs "example3">}}
{{< tab "C#" >}}
```csharp
// Method should match with ReleasePageStream delegate signature
private void UserReleaseStreamMethod(int pageNumber, Stream stream)
{
	Console.WriteLine($"Releasing memory for page: {pageNumber}");
    stream.Close();
}
 
using (Annotator annotator = new Annotator("input.pdf"))
{
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = $"D:/result_{pageNumber}.png";
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2, 3, 4 };
	previewOptions.Height = 100;
    previewOptions.Width = 80;
 
    // here we set delegate target method
    previewOptions.ReleasePageStream = UserReleaseStreamMethod;
    annotator.Document.GeneratePreview(previewOptions);   
}
```
{{< /tab >}}
{{< /tabs >}}

## Show and hide replies for WordsProcessing documents

Use the boolean [RenderComments](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/rendercomments/) property to show comments when rendering image preview.

{{< alert style="info" >}}This feature is supported for WordProcessign documents only.{{< /alert >}}

The default value of the property is `true`. To hide comments, set it to `false`. This property applies to all comments.

The following code snippet shows how to render an image preview without comments:

{{< tabs "example4">}}
{{< tab "C#" >}}
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
{{< /tab >}}
{{< /tabs >}}

## Generate cells preview with specified columns

GroupDocs.Annotation v20.11 and later allows you to specify the columns you want to generate on the sheet you selected. To do this, use the [WorksheetColumns](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/worksheetcolumns) property.

{{< alert style="info" >}}This feature is supported for CellsProcessign documents only.{{< /alert >}}

The following code snippet shows how to set the list of columns to render:

{{< tabs "example5">}}
{{< tab "C#" >}}
```csharp
PreviewOptions previewOptions =
    new PreviewOptions(pageNumber => new FileStream($"preview_pages/page{pageNumber}.png", FileMode.Create),
        (number, stream) => stream.Dispose());
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 2, 3));
previewOptions.WorksheetColumns.Add(new WorksheetColumnsRange("Sheet1", 1, 1));

using (Annotator annotator = new Annotator("input.xlsx"))
{
    annotator.Document.GeneratePreview(previewOptions);
}
```
{{< /tab >}}
{{< /tabs >}}

### Original worksheet
![](/annotation/net/images/original_page.png)
### Generated image file
![](/annotation/net/images/generated_page.png)