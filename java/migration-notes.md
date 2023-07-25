---
id: migration-notes
url: annotation/java/migration-notes
title: Migration Notes
weight: 4
description: ""
keywords: 
productName: GroupDocs.Annotation for Java
hideChildren: False
toc: True
---

## Why to migrate?

Here are the key reasons to use the new updated API provided by GroupDocs.Annotation for Java since version 19.8:
*   The `Annotator` class introduced as a single entry point to manage the document annotating process to any supported file format (instead of `AnnotationImageHandler` class in previous versions).
*   The overall rendering speed improved dramatically by saving rendered page as soon as it was rendered, not when all pages list were rendered.
*   Document saving options simplified so it is easy to instantiate proper options class and to control over document annotating and saving processes.

## How to migrate?

Here is a brief comparison of how to annotate document and save it using old and new API.

### Old coding style

{{< tabs "example1">}}
{{< tab "Java" >}} 
```java
List<AnnotationInfo> annotations = new List<AnnotationInfo>();
AnnotationInfo areaAnnotation = new AnnotationInfo();
areaAnnotation.setPageNumber(0);
areaAnnotation.setBox(new Rectangle(100, 100, 100, 100));
areaAnnotation.setType(Domain.AnnotationType.Area);
areaAnnotation.setText("area");

AnnotationInfo ellipseAnnotation = new AnnotationInfo();
ellipseAnnotation.setPageNumber(0);
ellipseAnnotation.setBox(new Rectangle(200, 200, 80, 80));
ellipseAnnotation.setType(Domain.AnnotationType.Ellipse);
ellipseAnnotation.setText("ellipse");           
 
// Create annotation config
AnnotationConfig config = new AnnotationConfig();

// Set storage path
config.setStoragePath("storage");

// Create annotation handler
AnnotationImageHandler annotator = new AnnotationImageHandler(config);

// Create input file
// Export annotations and save result
InputStream result = annotator.exportAnnotationsToDocument(fs, annotations);

// Save result stream to file.
OutputStream fileStream = new FileOutputStream("input.pdf");
IOUtils.copy(result, fileStream);
```
{{< /tab >}}
{{< /tabs >}}

### New coding style

{{< tabs "example2">}}
{{< tab "Java" >}} 
```java
// Create list of annotations
List<AnnotationBase> annotations = new List<AnnotationBase>();

AreaAnnotation areaAnnotation = new AreaAnnotation();
areaAnnotation.setPageNumber(0);
areaAnnotation.setBox(new Rectangle(100, 100, 100, 100));
areaAnnotation.setText("area");

EllipseAnnotation ellipseAnnotation = new EllipseAnnotation();
ellipseAnnotation.setPageNumber(0);
ellipseAnnotation.setBox(new Rectangle(200, 200, 80, 80));
ellipseAnnotation.setText("ellipse");
 
Annotator annotator = new Annotator("input.pdf");

// Add annotations
annotator.Add(annotations);

// Save result to "result.pdf"
annotator.Save("result.pdf", new SaveOptions());
```
{{< /tab >}}
{{< /tabs >}}
  
For more code snippets and specific use cases please refer to our [Developer Guide documentation]({{< ref "annotation/java/advanced-usage" >}}) or [GitHub](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java) samples and showcases.
