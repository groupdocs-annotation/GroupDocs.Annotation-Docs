---
id: get-supported-file-formats
url: annotation/net/get-supported-file-formats
title: Get supported file formats
weight: 1
description: "This article explains how to obtain supported file formats list when annotate documents and images with GroupDocs.Annotation within your .NET applications."
keywords: supported image formats, supported file formats, annotation, Groupdocs annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to get supported file formats info
        description: Learn how to get supported file formats step by step
        steps:
        - name: Interface IEnumerable
          text: FileType collection call
        - name: Iterate over elements in a FileType collection
          text: Using a foreach loop, iterate over the resulting collection.
toc: True
---
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/net) allows you to get the list of supported file formats. To do this, follow these steps:

1.   Call the [GetSupportedFileTypes](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/filetype/methods/getsupportedfiletypes) method of the [FileType](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/filetype) class.
2.   Enumerate through the collection of [FileType](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/filetype) objects.

The following code snippet shows how to get supported file formats list:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
IEnumerable<FileType> supportedFileTypes = FileType
	.GetSupportedFileTypes()
	.OrderBy(f => f.Extension);

foreach (FileType fileType in supportedFileTypes)
	Console.WriteLine(fileType);
```
{{< /tab >}}
{{< /tabs >}}
