---
id: generate-document-pages-preview
url: annotation/net/generate-document-pages-preview
title: Generate document pages preview
weight: 3
description: "Following this guide you will learn how to generate PDF, Word, Excel, PowerPoint documents thumbnails and preview document pages using GroupDocs.Annotation for .NET API."
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
---
[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) allows to generate document page previews using [GeneratePreview](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/document/methods/generatepreview) method of a [Document](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/properties/document) class.  
[PreviewOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions) class is used to manage preview generation process - specify desired page numbers, image format etc.

Here are the steps to generate document preview with GroupDocs.Annotation API:
*   Create a new instance of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class and pass source document path as a constructor parameter.
*   [Document](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/properties/document) property of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object allows to access source document and provides [GeneratePreview](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/document/methods/generatepreview) method.
*   Instantiate the [PreviewOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions) object with:
    *   delegate for each page stream creation (see event handler CreatePageStream); 
    *   image preview format - PNG / JPG / BMP,
    *   page numbers to process;
    *   custom size of preview images (if needed).  
{{< alert style="info" >}} Stream that were created by [CreatePageStream](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/createpagestream) delegate will be disposed automatically once after generation of preview image. If you need to implement custom image preview stream disposing you have to pass additional argument [ReleasePageStream](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/releasepagestream) to clean up resources.
{{< /alert >}}       
*   Call [GeneratePreview](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/document/methods/generatepreview) method of [Annotator.Document](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/properties/document) object and pass [PreviewOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions) to it.

    
Here a [PreviewOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/previewoptions) class main properties:
*   **[CreatePageStream](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/createpagestream)** - Delegate which defines method to create output page preview stream;
*   **[ReleasePageStream](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/releasepagestream)** - Delegate which defines method to remove output page preview stream. This is can be used when need advanced control for resources handling;
*   **[Width](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/width)** - Preview image width. This property used when need customize output image width;
*   **[Height](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/height)** - Preview image height. This property used when need customize output image height;
*   **[PageNumbers](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/pagenumbers)** - Page numbers that will be previewed;
*   **[PreviewFormat](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/previewformat)** - Gets or sets the preview image format which provides ability to choose between image quality and size. **BMP** format should be used for the best image quality. **JPG** format will be useful in case of strict requirements to image size - it produces smallest image size (and faster loading image previews), but with lower quality than **BMP**. By default **PNG** format is selected - which is a golden mean between image quality and size;
*   **[RenderComments](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/rendercomments)** - Default value is *true*. If it is not needed to display replies and comments at the page preview - set *RenderComments* property to *false* (replies and comments would still be stored inside your document).  
    Please notice, that *RenderComments* value will impact any document comments (doesn't matter if they were added by GroupDocs.Annotation or some other application). This property affects only on WordProcessing documents;
*   **[RenderAnnotations](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/renderannotations)** - Default value is *true*. If it is not needed to display annotations - set *RenderAnnotations* property to *false* (all annotations would still be stored inside your document).  
*   **[WorksheetColumns](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/worksheetcolumns)** - List of objects [WorksheetColumnsRange](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/worksheetcolumnsrange) that indicates which columns to generate on specified worksheet.

The following code snippet demonstrates how to generate document previews.

## Get document page previews 

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

## Set specific size for preview images

In some cases it may be useful to set specific image size during document pages preview generation. For example, to generate document pages thumbnails - small images that is a compressed preview image of the original image that is used as a placeholder. The main advantage of such thumbnail images is their reduced file size compared to the original page image.

The following code snippet demonstrates how to set specific size for preview images.

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

## Get page previews with manual resource cleaning

By default, after generating and rendering document page preview  image stream will be immediately disposed. However there is an ability to implement custom method for handling this operation.

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

## Show\\hide replies for WordsProcessing documents

If you need not to generate comments on image preview you may use *RenderComments* property

{{< alert style="info" >}}Supported for WordProcessign documents{{< /alert >}}

Default State is true. If needed not to generate replies and comments - set it as false. Please notice, that it concerns any comments it doesn't matter if they were added by GroupDocs.Annotation or somewhere else, they won’t be on the preview. But that still be present on the document.

Here the code that demonstrates how render image preview without comments:

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

## Generate Cells preview with specified columns

Starting from 20.11 version it is possible to specify columns you want to generate on the sheet you selected.
{{< alert style="info" >}}Supported only for CellsProcessign documents, other formats ignore this property{{< /alert >}}

The following code snippet demonstrates how to use [WorksheetColumns](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.options/previewoptions/properties/worksheetcolumns) property.

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
###
In the following images you can see how the columns were generated in the range from the second to the third and the first after them. Columns are generated in the order you specify, each column is generated only once, so please keep this in mind while using this feature.

### Original worksheet
![](annotation/net/images/original_page.png)
### Generated image file
![](annotation/net/images/generated_page.png)


## More resources

### GitHub Examples
You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Annotation for .NET examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
*   [GroupDocs.Annotation for Java examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java)
*   [Document Annotation for .NET MVC UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC)
*   [Document Annotation for .NET App WebForms UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms)
*   [Document Annotation for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Dropwizard)
*   [Document Annotation for Java Spring UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Spring)
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.