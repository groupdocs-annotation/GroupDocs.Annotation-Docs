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

## What is Version Control?

Version control is the method used tracking and recording changes in documents that occur over time. Versioning organizes the history of changes in a logical order, and allows for review or version rollbacks if needed.

In almost any business or organization, there will arise the need for changes in documents or files. Often, documents (whether paper or electronic) are passed around, and it is up to each individual to determine how to manage the changes. More frequently, individuals have their own separate and unique ways of tracking versions. It is not hard to see how this can quickly create confusion and disorder.

GroupDocs.Annotation as a document management system has it's own versioning mechanism. It solves the problems of tracking changes by retaining versions inside a document. So, our annotator allows you not only to add or remove annotations, but also to rollback and get all changes that were applied to this document using our .NET API.

## How it works in .NET API

Every time you are saving file using [Annotator.Save()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method - you implicitly create a new version of the annotated file. Versions list stores not document, it keeps annotations that you add, remove, and change. When you are opening a file, by default the latest lervsion os the document is laoded. So you can easily swap between different changes made with GroupDocs.Annotation. And of course you can set your own version names.


## Working with versioning in .NET API

### Add Version with custom name

If you want to swap between versions easily you might need to have ability to set custom versions names.
In this scenario, you can label specific versions to represent status and relevance. This approach enables other people to find a specific version for a particular state in the editing process.

Here the code that demonstrates how to save version with custom name:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	annotator.Update(new AreaAnnotation{ Box = new Rectangle(100, 100, 100, 100) });
	annotator.Save("result.pdf", new SaveOptions { Version = "CUSTOM_VERSION" });
}
```
{{< alert style="info" >}}
Type of [Version](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/saveoptions/properties/version) property is object, so it support any type, and you can use any variable as version variable
{{< /alert >}}


### Get List of All version keys on a document
If you don't know what versions were added earlier or want to know versions count, this paragraph is for you. With our annotator you can easily get all previous version by running just 1 line of code. You could do this by calling [GetVersionsList](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method of [Annotator](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator) object:

Here the code that demonstrates how to get list of versions keys:
```csharp
using (Annotator annotator = new Annotator("result.pdf")) { 
      List<object> versionKeys = annotator.GetVersionsList();
}
```
{{< alert style="info" >}}
[Annotator.GetVersionList()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) returns list of objects because it supports any type of key. But if you used some specified keys as string - you can convert it.
{{< /alert >}}


### Get List of Annotations using version key
If you need to get list of annotations you can use [Annotator.GetVersion()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method.


Here code that demonstrates how to get list of annotations from specific version of document
```csharp
using (Annotator annotator = new Annotator("result.pdf"))
{
    List<AnnotationBase> annotations = annotator.GetVersion("CUSTOM_VERSION");
}
```
{{< alert style="info" >}}
[GetVersion](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) supports any type, and you can use any variable as version.
{{< /alert >}}


### Load Document of custom Version
Using [LoadOptions.Version](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/properties/version) property you could load specific version of annotated document.


Here the code that demonstrates how load version using version property:
```csharp
 using (Annotator annotator = new Annotator($"result.{ext}", new LoadOptions { Version = "CUSTOM_VERSION" }))
{
	annotator.Save("result_loaded.pdf");
}
```

## Conclusion

In short, we have learned how to work with document versioning using .NET API. We have shown how you can name our versions, how to get all existed versions, how to get all changes by version name, and how to to load a specific version of the document. We have covered most important part of our .NET API functionality. Now, you should be confident to build your own document annotator .NET application. 

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/net/developer-guide/advanced-usage/_index.md" >}}).
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
