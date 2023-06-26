---
id: generate-document-pages-preview
url: annotation/java/generate-document-pages-preview
title: Generate document page preview
weight: 3
description: "The page describes how to generate PDF, Word, Excel, PowerPoint documents thumbnails and preview document pages using GroupDocs.Annotation for Java API."
keywords: Preview document pages, Document pages as PNG, document pages as JPG, Document preview
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
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

GroupDocs.Annotation allows you to generate document page previews. To do this, call the [generatePreview](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/document/#generatePreview-com.groupdocs.annotation.options.pagepreview.PreviewOptions-) method of the [Document](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/document/) class. 

Use the [PreviewOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/) class to manage the preview generation process: specify desired page numbers, image format, etc.

To generate a document preview, follow these steps:
1.  Create an instance of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the source document path as a parameter. The [Document](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/document/) property of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class provides access to source document and implements [generatePreview](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/document/#generatePreview-com.groupdocs.annotation.options.pagepreview.PreviewOptions-) method.
3.   Instantiate the [PreviewOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/) class. Follow these steps:
    a.   for each page, delegate stream creation (see the [CreatePageStream](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/createpagestream/) event handler); 
    b.   specify the image preview format - PNG / JPG / BMP,
    c.   specify page numbers to process;
    d.   set the custom size of preview images (if needed).  
{{< alert style="info" >}} Stream created by the [CreatePageStream](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/createpagestream/) delegate are disposed automatically once after generation of preview image. To implement the custom image preview stream disposing, you have to specify an additional argument [ReleasePageStream](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/releasepagestream/) to clean up resources.
{{< /alert >}}       
4.  Call the [generatePreview](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/document/#generatePreview-com.groupdocs.annotation.options.pagepreview.PreviewOptions-) method of the [Document](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/document/) class. Specify [PreviewOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/).

    
The [PreviewOptions](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/) class main properties are as follows:
*   [CreatePageStream](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/createpagestream/) is a delegate which defines the method to create output page preview stream.
*   [ReleasePageStream](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/releasepagestream/) is a delegate which defines the method to remove output page preview stream. Use it for advanced control for resources handling.
*   [Width](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/#setWidth-int-) specifies the preview image width.
*   [Height](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/#setHeight-int-) specifies the preview image height.
*   [PageNumbers]https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/#setPageNumbers-int---) - Page numbers that will be previewed;
*   [PreviewFormat](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/#setPreviewFormat-int-) gets or sets the preview image format. Use the BMP format should be used for the best image quality. Use the JPG format in case of strict requirements to image size, but with lower quality than BMP. By default GroupDocs.Annotation uses the PNG format which is a golden mean between image quality and size.
*   [RenderComments](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/#setRenderComments-boolean-) is an option to show or hide comments. By default it is `true`. Set it to `false` if you do not need to show comments. This property affects only on WordProcessing documents. The `RenderComments` value impacts any document comments.
*   [RenderAnnotations](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/#setRenderAnnotations-boolean-) is an option to show or hide annotations.By default it is `true`. Set it to `false` if you do not need to show annotations.
*   [WorksheetColumns](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/previewoptions/#setWorksheetColumns-java.util.List-com.groupdocs.annotation.options.pagepreview.WorksheetColumnsRange--) is a list of the `WorksheetColumnsRange` objects that indicates which columns to generate on specified worksheet.

The following code snippet demonstrates how to generate document previews.

## Get document page previews 

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates annotating generating previews from document
Annotator annotator = new Annotator("inputPath");

// Create an instance of PreviewOptions class
PreviewOptions previewOptions = new PreviewOptions(new CreatePageStream() {
    @Override
    public OutputStream invoke(int pageNumber) {
        try {
            // Set several file name
            String fileName = "OutputPath_"+pageNumber+".png";
            OutputStream result = new FileOutputStream(fileName);
            return result;
        } catch (Exception ex) {
            throw new GroupDocsException(ex);
        }
    }
});

previewOptions.setPreviewFormat(PreviewFormats.PNG);

previewOptions.setPageNumbers(new int[]{1, 2, 3});

// Generate preview for documents
annotator.getDocument().generatePreview(previewOptions);
```
{{< /tab >}}
{{< /tabs >}}

## Set specific size for preview images

You can set a specific size for preview images. For example, you can create small-sized thumbnails and full-sized previews.

The following code snippet shows how to set specific size for preview images:

{{< tabs "example2">}}
{{< tab "Java" >}}
```java
// This example demonstrates annotating generating previews from document
Annotator annotator = new Annotator("inputPath");

// Create an instance of PreviewOptions class
PreviewOptions previewOptions = new PreviewOptions(new CreatePageStream() {
    @Override
    public OutputStream invoke(int pageNumber) {
        try {
            // Set several file name
            String fileName = "OutputPath_"+pageNumber+".png";
            OutputStream result = new FileOutputStream(fileName);
            return result;
        } catch (Exception ex) {
            throw new GroupDocsException(ex);
        }
    }
});

previewOptions.setPreviewFormat(PreviewFormats.PNG);
previewOptions.setPageNumbers(new int[] { 1, 2, 3, 4 });
previewOptions.setHeight(100);
previewOptions.setWidth(80);

// Generate preview for documents
annotator.getDocument().generatePreview(previewOptions);
```
{{< /tab >}}
{{< /tabs >}}