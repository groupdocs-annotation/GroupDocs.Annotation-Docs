---
id: versioning-of-documents
url: annotation/net/versioning-of-documents
title: Versioning of annotated documents
weight: 3
description: "Following this guide you will learn how to manage different versions of document using GroupDocs.Annotation for .NET API."
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

Every time you are saving file using [Annotator.Save()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/save/index) method - you implicitly create a new version of the annotated file. Versions list stores not document, it keeps annotations that you add, remove, and change. So you can easy swap between different changes made with GroupDocs.Annotation. And of course you can set your version names.

By default, they are created using unique GUID keys. Next, each aspect of using versions will be considered. The API execution logic has not changed, so you do not need to change your code to use it as before. The latest version of document is loaded by default. 

### Backward Compatibility

The update is fully compatible with previous and next updates (The latest saved version will be used), however, using versions on previous versions is not possible and the list of versions in this document will not be changed. And If you update file from 20.4+ using 20.2 and lower few times, after loading this document on 20.4+ only last changes will be added as new version.

### Add Version with custom name

If you want to swap between versions easily you might need to have ability to set custom versions names.

  
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
## Get List of All version keys on a document
If you don't know what versions were added earlier or want to know versions count 
Here the code that demonstrates how to get list of versions keys, you could do this calling [GetVersionsList](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method of [Annotator](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator):
```csharp
using (Annotator annotator = new Annotator("result.pdf")) { 
      List<object> versionKeys = annotator.GetVersionsList();
}
```
{{< alert style="info" >}}
[Annotator.GetVersionList()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) returns list of objects because it supports any type of key. But if you used some specified keys as string - you can convert it.
{{< /alert >}}
## Get List of Annotations using version key
If you need to get list of annotations you can use [Annotator.GetVersion()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/getversionslist) method
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
## Load Document of custom Version
Using [LoadOptions.Version](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/properties/version) property you could load specific version of annotated document
Here the code that demonstrates how load version using version property:
```csharp
 using (Annotator annotator = new Annotator($"result.{ext}", new LoadOptions { Version = "CUSTOM_VERSION" }))
{
	annotator.Save("result_loaded.pdf");
}
```
## More resources
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
