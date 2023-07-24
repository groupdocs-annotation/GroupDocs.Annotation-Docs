---
id: versioning-of-documents
url: annotation/java/versioning-of-documents
title: Versioning of annotated documents
weight: 3
description: "The page describes how to manage different versions of document using GroupDocs.Annotation for Java API."
keywords: Get different document versions, versions, Version management
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
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

When you save a file using the [Annotator.save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method, the GroupDocs.Annotations creates a version of the annotated file. Versions list keeps annotations that you add, remove, and change. You can swap between different changes made with GroupDocs.Annotation. If needed, you can set your version names.

By default, GroupDocs.Annotations names version using a GUID. You can specify a custom version name.

### Add version with custom name

You can specify a custom version name.
  
The following code snippet shows how to save version with custom name:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to add version.

// Create an instance of Annotator class
try (Annotator annotator = new Annotator("input.pdf")) {
    // Create an instance of AreaAnnotation class and set options
    AreaAnnotation areaAnnotation = new AreaAnnotation();
    areaAnnotation.setBox(new Rectangle(100, 100, 100, 100)); 
    annotator.update(areaAnnotation);
    SaveOptions saveOptions = new SaveOptions();
    saveOptions.setVersion("CUSTOM_VERSION");
    
    // Save to file
    annotator.save("result.pdf", saveOptions);
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
The [Version](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation.options/saveoptions/) property is object.
{{< /alert >}}

## Get the list of version keys of a file

To get the list of version keys, call the [Annotator.getVersionList()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#getVersionsList--) method of the [Annotator](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/) class.

The following code snippet shows how to get list of versions keys:

{{< tabs "example2">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to get list of all version keys on a document.

// Create an instance of Annotator class
try (Annotator annotator = new Annotator("input.pdf")) {
    // Get versions lest from annotated file
    List<Object> versionKeys = annotator.getVersionsList();
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
The [Annotator.GetVersionList()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#getVersionsList--) method returns list of objects. If needed, you can convert them to appropriate type.
{{< /alert >}}

## Get the list of annotations using version key

To get the list of annotations in a specific version, call the [Annotator.getVersion()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#getVersion-java.lang.Object-) method of the [Annotator](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/) class.

The following code snippets shows how to get list of annotations in a specific version:

{{< tabs "example3">}}
{{< tab "Java" >}}
```java
// This example demonstrates how get list of annotations using version key.

// Create an instance of Annotator class
try (Annotator annotator = new Annotator("input.pdf")) {
    // Get versions lest from annotated file by CUSTOM_VERSION
    List<AnnotationBase> annotations = annotator.getVersion("CUSTOM_VERSION");
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
The [Annotator.getVersion](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#getVersion-java.lang.Object-) method returns list of objects. If needed, you can convert them to appropriate type.
{{< /alert >}}

## Load a specific file version

To load a specific version of a file, call the [LoadOptions.version()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.options/loadoptions/#setVersion-java.lang.Object-) method and specify the version key.

The following code snippets shows how load version using version property:

{{< tabs "example4">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to load document of custom version.

// Create an instance of Annotator class and set custom version
LoadOptions loadOptions = new LoadOptions();
loadOptions.setVersion("CUSTOM_VERSION");

// Create an instance of Annotator class
try (Annotator annotator = new Annotator("input.pdf", loadOptions)) {
    
    // Save to file
    annotator.save("result_loaded.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}