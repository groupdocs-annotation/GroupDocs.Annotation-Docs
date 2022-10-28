---
id: document-text-info
url: annotation/net/document-text-info
title: Getting information about document content
weight: 4
description: "Following this guide you will learn how to get an information about document content using GroupDocs.Annotation for .NET API."
keywords: Text line information, text coordinates, document content
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

Since version 21.3 the structure [PageInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) has been changed. Now you can get an information not only about the width and height of each page, but also about it text content. In addition to that, page numbering was also added to the [PageInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) structure. You can now take an advantage of the new functionality by calling the [GetDocumentInfo()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/document/methods/getdocumentinfo) method of the [Document](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/document) class.

Each page, represented by [PageInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) structure, now contains list of [TextLineinfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/textlineinfo). Every [TextLineinfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/textlineinfo) contains information about text top and left indents, width, height and text itself. In other words, we can say that each page is represented as a sequence of text lines. Every text line is described by its parameters (width, heigh and indents).

**All numerical specifications are presented in pixels relative to the top left-hand corner of the page.**

Code example below shows how you can get data from described structures:

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


### Supported formats

The ability to retrieve text information is implemented for most supported formats: word, pdf, excel, visio diagrams, power point presentations, html and email. Text retrieval works for all formats as it is, except for html (.htm, .html etc) and email (.eml, .msg etc). With those formats it works by converting them into the word document (.docx). Therefore, text parameters for these formats corresponds to their word counterparts.


### How it works

Example below shows how these parameters are calculated:

 ![Example of how text parameters are calucalated](/annotation/net/images/highlighted-text.png)

***Example above is schematic, although it's quite accurate.***

Imagine you have a text part like the one in the picture. Each text line may be represented filled into rectangle. Width and height of this rectangle is the width and height of the text, and the indentation from the top left corner of the page to the border of this rectangle is top and left indents. 

In the illustration above, the possible text rectangles are marked in black. The arrows indicate corresponding text parameters. 

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
