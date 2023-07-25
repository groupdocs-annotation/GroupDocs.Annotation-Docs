---
id: get-supported-file-formats
url: annotation/java/get-supported-file-formats
title: Get supported file formats
weight: 1
description: "This page describes how to obtain supported file formats list when annotate documents and images with GroupDocs.Annotation within your .NET applications."
keywords: supported image formats, supported file formats, annotation, Groupdocs annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
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
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/java) allows you to get the list of supported file formats. To do this, follow these steps:

1.   Call the [getSupportedFileTypes](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options/filetype/#getSupportedFileTypes--) method of the [FileType](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options/filetype/) class.
2.   Enumerate through the collection of [FileType](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options/filetype/) objects.

The following code snippet shows how to get supported file formats list:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates file types support

// Get list of supported file
List<FileType> fileTypes = FileType.getSupportedFileTypes();
Iterator tmp0 = (fileTypes).iterator();

// Iterating elements and print file types
while (tmp0.hasNext()) {
    FileType fileType = (FileType) tmp0.next();
    System.out.println(fileType.getExtension());
}
```
{{< /tab >}}
{{< /tabs >}}
