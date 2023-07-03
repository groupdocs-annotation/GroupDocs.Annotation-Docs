---
id: change-image-quality
url: annotation/net/change-image-quality
title: Set image quality
weight: 10
description: "The page describes how to set the quality of an image added to a document."
keywords: image quality, set
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
toc: True
---

GroupDocs.Annotation v22.4 and later allows you to set the quality of an image added to a document. To do this, specify the `imageQuality` parameter of the [AddImageToDocument](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/document/addimagetodocument/) method.

The parameter value is from 1 to 100. 1 means the lowest resolution, and 100 means the highest.

The following code snippet shows how to set the image quality:

{{< tabs "example1">}}
{{< tab "C#" >}} 
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
{{< /tab >}}
{{< /tabs >}}
