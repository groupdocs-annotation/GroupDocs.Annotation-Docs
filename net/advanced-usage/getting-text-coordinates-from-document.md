---
id: document-text-info
url: annotation/net/document-text-info
title: Get the document content information
weight: 4
description: "This page describes how to get an information about document content using GroupDocs.Annotation for .NET API."
keywords: text, line, information, coordinates, document, content
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How getting text coordinates from document
        description: Learn how getting text coordinates from document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Interface document info
          text: Create an object of the IDocumentInfo interface and assign document information to it.
        - name: Get page information
          text: Using a foreach loop to get information about each page
toc: True
---

GroupDocs v21.3 and later allows you to get information not only about the width and height of any page but also about page number and text content. To do this, use the [PageInfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) structure by calling the [GetDocumentInfo()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/document/methods/getdocumentinfo) method of the [Document](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/document) class.

The [PageInfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) structure represents each page and contains the list of [TextLineinfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/textlineinfo). Every [TextLineinfo](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/textlineinfo) stores text top and left indents, width, height and the text itself. This way, each page is represented as a sequence of text lines. Every text line is described by its parameters (width, height, and indents).

The following code snippet shows how to get data from described structures:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.docx"))
{
    IDocumentInfo documentInfo = annotator.Document.GetDocumentInfo();

    foreach (PageInfo page in documentInfo.PagesInfo)
    {
        //Here you can access PageInfo fields
        Console.WriteLine("Page number {0}, width: {1} and height: {2}", page.PageNumber, page.Width, page.Height);

        foreach (TextLineInfo textLine in page.TextLines)
        {
            //Here you can access TextLineInfo fields
            Console.WriteLine("\tText line. '{0}'", textLine.Text);
            Console.WriteLine("\t\tText width {0} and height {1}. Top indent: {2}, left indent: {3}", 
                textLine.Width, textLine.Height, textLine.TopIndent, textLine.LeftIndent);
        }
    }
}
```
{{< /tab >}}
{{< /tabs >}}

### Supported formats

The GroupDocs.Annotation allows you to retrieve text information from files of the following formats: Word, PDF, Excel files, Visio diagrams, PowerPoint presentations, HTML, and email. You can retrieve text directly from files of all specified formats except of HTML (.htm, .html, etc.) and email (.eml, .msg, etc.). To retrieve text from HTML and email files, GroupDocs.Annotation converts them to .docx.

### Description of text parameters

Example below shows how these parameters are calculated:

 ![Example of how text parameters are calculated](/annotation/net/images/highlighted-text.png)


The possible text rectangles are marked in black. The arrows indicate corresponding text parameters. 