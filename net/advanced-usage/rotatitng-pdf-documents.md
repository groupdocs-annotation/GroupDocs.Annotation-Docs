---
id: rotatitng-pdf-documents
url: annotation/net/rotatitng-pdf-documents
title: Rotating PDF documents
weight: 10
description: "The page describes how to rotating the PDF document pages using GroupDocs.Annotation for .NET API."
keywords: Rotate
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to rotate pdf documents
        description: Learn how to rotate pdf documents text step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Property document
          text: Specify document properties
        - name: Save document
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---

GroupDocs.Annotation v21.12 and later allows you to rotate the page of a PDF document by 90, 180, 270 degrees clockwise. To do this, set the [ProcessPages](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/processpages/) property to page number and then set the [Rotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/rotation/) property to one of the following values:
* None - does not rotate the document
* on90 - rotate the document 90 degrees clockwise
* on180 - rotate the document 180 degrees clockwise
* on270 - rotate the document 270 degrees clockwise

By default, the property is set to `None`.

The following code snippets shows how to rotate the first page by 90 degrees clockwise:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("annotated_file.pdf"))
{
	annotator.ProcessPages = 1;
	annotator.Rotation = RotationDocument.on90;
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}