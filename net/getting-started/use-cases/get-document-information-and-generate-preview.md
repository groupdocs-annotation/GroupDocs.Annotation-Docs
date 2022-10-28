---
id: how-to-get-document-information-and-generate-preview
url: annotation/net/how-to-get-document-information-and-generate-preview
title: How to get PDF document information and generate preview
weight: 4
description: "Programmatically extract information from PDF document. Generate document preview using .NET API."
keywords: extract text information, get text lines, preview PDF, get text from PDF
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to programmatically read text from PDf documents
    showVideo: False
    howTo:
        name: How to extract text from PDF document
        description: Learn how to programmatically get text information line by line
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

When working with a PDF document programmatically, in addition to interacting with the text via annotations, the ability to access the text as such is very important. The opportunity to scan the text and to split it into pages, paragraphs and lines is an essential tool. Our .NET API provides this capability. By uploading a PDF document you can receive its full text page by page and even line by line within seconds! All you need to do is write a few lines of code. 

### Example

Since version 21.3 the structure [PageInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) has been changed. You can now take an advantage of the new functionality by calling the [GetDocumentInfo()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/document/methods/getdocumentinfo) method of the [Document](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/document) class.

Each page, represented by [PageInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) structure, now contains list of [TextLineinfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/textlineinfo). Every [TextLineinfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/textlineinfo) contains information about text top and left indents, width, height and text itself. In other words, we can say that each page is represented as a sequence of text lines and you can get this information programatically within seconds!

Code example below shows how you can get data from described structures:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    IDocumentInfo documentInfo = annotator.Document.GetDocumentInfo();

    foreach (PageInfo page in documentInfo.PagesInfo)
    {
        // Here you can access PageInfo fields
        Console.WriteLine("Page number {0}, width: {1} and height: {2}", page.PageNumber, page.Width, page.Height);

        foreach (TextLineInfo textLine in page.TextLines)
        {
            // Here you can access TextLineInfo fields
            Console.WriteLine("\tText line. '{0}'", textLine.Text);
        }
    }
}
```

### Supported formats

The ability to retrieve text information is implemented for most supported formats: word, pdf, excel, visio diagrams, power point presentations, html and email. Text retrieval works for all formats as it is, except for html (.htm, .html etc) and email (.eml, .msg etc). With those formats it works by converting them into the word document (.docx). Therefore, text parameters for these formats corresponds to their word counterparts.

## Generate document preview


When annotating a document, it is very important to be able to see how the document would look in printed form. After all, most documents end up on paper. Of course, this can be achieved by standard means - opening the document and sending it to print. Modern operating systems usually show a preview of a document before printing it. But what if it needs to be done programmatically and much faster? 

Our .NET API makes it possible. You can generate a preview right after annotating. This can be achieved by writing just a few lines of code: 

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

You can learn about more properties and setting that our [preview generator](https://docs.groupdocs.com/annotation/net/generate-document-pages-preview/) provies. It is much more configurable than we have shown above, but due to the article limitations we cannot cover all the details here.


## Conclusion

In short, you have learned how extract data from PDF document within .NET applications. Further, you have seen how to generate preview of any PDF file. Now, you should be confident to build your own document annotator .NET application. 

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/net/developer-guide/advanced-usage/_index.md" >}}).
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
