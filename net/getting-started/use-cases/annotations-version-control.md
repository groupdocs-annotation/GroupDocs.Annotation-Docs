---
id: how-to-control-versions-of-annotations
url: annotation/net/how-to-control-versions-of-annotations
title: How to control different versions of annotations in .NET
weight: 5
description: "Programmatically add new annotation verions, rollback to previous version, control document versions using .NET API."
keywords: versioning document, document versions, version control, annotations.
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to get get list of all version keys using .NET API.
    showVideo: False
    howTo:
        name: How to add text annotations
        description: Learn how to add text field and strikeout annotations to the PDF document
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Call method to get all versions of the document
            text: On annotator instance call GetVersionsList() method
          - name: Get all version keys of the document
            text: Save list of objects got from GetVersionList() method
toc: True
---

## Overview

Version control is used to track and record changes to documents. Versioning allows you to keep a history of changes to refer to a specific version when needed.

GroupDocs.Annotation implements a versioning mechanism. Thus, it allows you to add or remove annotations, as well as view the history of annotations added to a document using the .NET API.

## How it works in the .NET API

Every time you save a file using the [Annotator.Save()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method, you create a new version of the annotated file. The version list stores the annotations you add, remove, and change. When you open a file, the latest version of the document is loaded by default. If necessary, you can switch between different versions created with GroupDocs.Annotation.


## Working with versioning in .NET API

### Add a version with custom name

To swap between versions, set the custom version names on saving. So, you label specific versions to refer to them later.

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
The [Version](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions/properties/version) property is an object, so it support any type of version key.
{{< /alert >}}


### Get list of all document versions

To get the list of the document versions, call the [Annotator.GetVersionsList](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method of the [Annotator](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) class.

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
The [Annotator.GetVersionList()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method returns a list of objects to support keys of any type. If needed, cast it to the appropriate type.
{{< /alert >}}


### Get List of Annotations using version key

To get the list of annotations, use the [Annotator.GetVersion()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method of the [Annotator](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) class.


The following code snippet shows how to get list of annotations in a specific document version.

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
The [GetVersion](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) supports any type of version key.
{{< /alert >}}


### Load the custom version

To load the specific version, specify the [LoadOptions.Version](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/properties/version) property.


The following code snippet shows how to load the specific version using the `Version` property:

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