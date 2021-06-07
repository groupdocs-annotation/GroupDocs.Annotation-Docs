---
id: get-file-info
url: annotation/net/get-file-info
title: Get file info
weight: 2
description: "This article explains how to detect document file type, size and calculate pages count when annotate documents or images with GroupDocs.Annotation."
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
GroupDocs.Annotation allows to get document information which includes.

*   [FileType](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/idocumentinfo/properties/filetype) - document file type (PDF, Word document, Excel spreadsheet, PowerPoint presentation or image etc.);
*   [PageCount](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/idocumentinfo/properties/pagecount) - count of document pages;
*   [FileSize](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/idocumentinfo/properties/size) - document file size;

[PagesInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/idocumentinfo/properties/pagesinfo) represents List of [PageInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) objects which store information about each page. 

[PageInfo](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo) has two properties - [Width](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo/properties/width) and [Height](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models/pageinfo/properties/height) in pixels. This properties works with all formats except Email And Html that doesn't have height and width so the won't store them and will be empty. All pages width and height will be same in all formats except Cells, so you can use size of first element as size of all document.

The following code sample demonstrates how to get information about document and Width and Height of its pages:

```csharp
//Get file info for the file from local disk
using (Annotator annotator = new Annotator("input.docx"))
{
	IDocumentInfo info = annotator.Document.GetDocumentInfo();
    int width = info.PagesInfo[0].Width;
    int height = info.PagesInfo[0].Height;
    Console.WriteLine("\nFile type: {0}\nNumber of pages: {1}\nDocument size: {2} bytes", info.FileType, info.PageCount, info.Size);
}
```

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/net/developer-guide/advanced-usage/_index.md" >}}).

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
