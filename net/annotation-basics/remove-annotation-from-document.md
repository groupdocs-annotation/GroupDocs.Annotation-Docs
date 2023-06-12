---
id: remove-annotation-from-document
url: annotation/net/remove-annotation-from-document
title: Remove annotation from document
weight: 5
description: "Learn how to remove annotations from document when collaborate, edit and annotate documents using GroupDocs.Annotation for .NET."
keywords: Delete annotation, remove annotation, annotate document
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to get file info
        description: Learn how to get file info step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Method Remove
          text: Call Annotator class method .Remove()
        - name: Save document
          text: Call Annotator class method .Save() and pass output path file to it.
toc: True
---
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/net) allows you to remove all previously added annotations. To do this, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [SaveOptions](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) class. Set `AnnotationTypes = AnnotationType.None`.
3.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

## Remove annotation using its index

The following code snippet shows how to remove annotation using its index:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("result.xlsx"))
{
	annotator.Remove(0);
	annotator.Save("removed.xlsx");
}
```
{{< /tab >}}
{{< /tabs >}}

## Remove annotation using the object

The following code snippet shows how to remove annotation using the object:

{{< tabs "example2">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("result.xlsx"))
{
	var tmp = annotator.Get();
	annotator.Remove(tmp[0]);
	annotator.Save("removed.xlsx");
}
```
{{< /tab >}}
{{< /tabs >}}

## Remove annotations using the list of indexes

The following code snippet shows how to remove annotations using list of indexes:

{{< tabs "example3">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("result.xlsx"))
{
	var idList = new List<int>{1, 2, 3};
	annotator.Remove(idList);
	annotator.Save("removed.xlsx");
}
```
{{< /tab >}}
{{< /tabs >}}

## Remove annotations using the list of objects

The following code snippet shows how to remove some annotations from document using list of objects:

{{< tabs "example4">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("result.xlsx"))
{
	var tmp = annotator.Get();
	annotator.Remove(tmp);
	annotator.Save("removed.xlsx");
}
```
{{< /tab >}}
{{< /tabs >}}