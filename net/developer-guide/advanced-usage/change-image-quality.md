---
id: change-image-quality
url: annotation/net/change-image-quality
title: Change image quality
weight: 10
description: "Following this guide you will learn how to change image quality using and add to document GroupDocs.Annotation for .NET API."
keywords: Change image quality
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to change image quality
        description: Learn how to change image quality step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Variables
          text: Create variables path to the inut PDF file, path to the JPG file, page number, image quality.
        - name: Saving a document
          text: Call the annotator method .AddImageToDocument and pass the created variables to it.
---

Starting from version 22.4 it is possible to change quality of image representation of document by setting property

**imageQuality** - where the value from 1 to 100. 1 means lowest resolution, 100 means highest

Here is the example of the code:


```csharp
using (Annotator annotator = new Annotator("input.pdf-file")) // specify the path to the input PDF file
{
	string dataDir = "input.pdf"; // specify the path to the input PDF file
    string data = "image.jpg"; // the path to the JPG file
    int pageNumber = 1; // set the page where the image will be inserted
    int imageQuality = 10; // set image quality from 1 to 100
    annotator.Document.AddImageToDocument(dataDir, data, pageNumber, imageQuality);
}
```

## More resources
### GitHub Examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Annotation for .NET examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
