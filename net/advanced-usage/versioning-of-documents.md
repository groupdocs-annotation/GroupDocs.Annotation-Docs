---
id: versioning-of-documents
url: annotation/net/versioning-of-documents
title: Versioning of annotated documents
weight: 3
description: "The page describes how to manage different versions of document using GroupDocs.Annotation for .NET API."
keywords: Get different document versions, versions, Version management
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to set document preview resolution
        description: Learn how to set document preview resolution step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Update
          text: In the .Update() method, create an instance of the annotation class and set its coordinates using the Box class.
        - name: Save document
          text: Call Annotator class .Save() method and pass output path file and instance of the SaveOptions class and set the version.
toc: True
---

When you save a file using the [Annotator.Save()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method, the GroupDocs.Annotations creates a version of the annotated file. Versions list keeps annotations that you add, remove, and change. You can swap between different changes made with GroupDocs.Annotation. If needed, you can set your version names.

By default, GroupDocs.Annotations names version using a GUID. If needed, you can specify a custom version name.

### Add version with custom name

You can specify a custom version name.
  
The following code snippet shows how to save version with custom name:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	annotator.Update(new AreaAnnotation{ Box = new Rectangle(100, 100, 100, 100) });
	annotator.Save("result.pdf", new SaveOptions { Version = "CUSTOM_VERSION" });
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
The [Version](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions/properties/version) property is object.
{{< /alert >}}

## Get the list of version keys of a file

To get the list of version keys, call the [GetVersionsList](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method of the [Annotator](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) class.

The following code snippet shows how to get list of versions keys:

{{< tabs "example2">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("result.pdf")) { 
      List<object> versionKeys = annotator.GetVersionsList();
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
The [Annotator.GetVersionList()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method returns list of objects. If needed, you can convert them to appropriate type.
{{< /alert >}}

## Get the list of annotations using version key

To get the list of annotations in a specific version, call the [Annotator.GetVersion()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method of the [Annotator](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) class.

The following code snippets shows how to get list of annotations in a specific version:

{{< tabs "example3">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("result.pdf"))
{
    List<AnnotationBase> annotations = annotator.GetVersion("CUSTOM_VERSION");
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
The [GetVersion](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method returns list of objects. If needed, you can convert them to appropriate type.
{{< /alert >}}

## Load a specific file version

To load a specific version of a file, specify the [LoadOptions.Version](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/properties/version) property.

The following code snippets shows how load version using version property:

{{< tabs "example4">}}
{{< tab "C#" >}}
```csharp
 using (Annotator annotator = new Annotator($"result.{ext}", new LoadOptions { Version = "CUSTOM_VERSION" }))
{
	annotator.Save("result_loaded.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}