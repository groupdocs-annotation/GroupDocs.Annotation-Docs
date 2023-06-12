---
id: how-to-get-document-information-and-generate-preview
url: annotation/net/how-to-get-document-information-and-generate-preview
title: How to get PDF document information and generate preview
weight: 4
description: "Extract text information from the PDF document. Generate document preview using .NET API."
keywords: extract text information, get text lines, preview PDF, get text from PDF
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to get text from the PDf documents
    showVideo: False
    howTo:
        name: How to extract text from PDF document
        description: Learn how to get text information line by line
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Extract document info from annotator
            text: On annotator instance get Document.GetDocumentInfo() data
          - name: Save this data to another variable
            text: Assign extracted data to the variable
          - name: Iterate over each page
            text: Get information about the page by accessing PagesInfo property
          - name: Interate over TextLines
            text: Get information about each text line by accessing TextLines property on the PageInfo object
toc: True
---


## Extract text information from PDf

Since version 21.3, GroupDocs.Annotation allows you to split the text of a PDF document into pages, paragraphs, and lines and recognize it.

To access the text information of the PDF document, call the [GetDocumentInfo()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/document/methods/getdocumentinfo) method of the [Document](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/document) class.

The [PageInfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) structures represent pages of the PDF document. Each structure contains a list of the [TextLineinfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/textlineinfo) structures. The [TextLineinfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/textlineinfo) structure contains information about text's top and left indents, width, height, and text itself.

The following code snippet shows how you can get data from described structures:

{{< tabs "example1">}}
{{< tab "C#" >}} 
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    IDocumentInfo documentInfo = annotator.Document.GetDocumentInfo();

    foreach (PageInfo page in documentInfo.PagesInfo)
    {
        // Access PageInfo fields
        Console.WriteLine("Page number {0}, width: {1} and height: {2}", page.PageNumber, page.Width, page.Height);

        foreach (TextLineInfo textLine in page.TextLines)
        {
            // Access TextLineInfo fields
            Console.WriteLine("\tText line. '{0}'", textLine.Text);
        }
    }
}
```
{{< /tab >}}
{{< /tabs >}}

You can get text information from Word, PDF, and Excel files, Visio diagrams, PowerPoint presentations, HTML pages, and emails. To get information from the HTML (.htm, .html, etc.) pages and emails (.eml, .msg, etc.), GroupDocs.Annotation converts them to the Word document (.docx).

## Generate document preview

GroupDocs.Annotation allows you to create page images (PNG, JPG, PDF) to preview the annotated document. 

The following code snippet shows how to create PNG images of the document's pages:

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
    annotator.Document.GeneratePreview(previewOptions);
}
```
{{< /tab >}}
{{< /tabs >}}

For details, see the [Create document's preview](https://docs.groupdocs.com/annotation/net/generate-document-pages-preview/) page.

