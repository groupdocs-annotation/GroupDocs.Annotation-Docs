---
id: migration-notes
url: annotation/net/migration-notes
title: Migration Notes
weight: 3
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
### Why To Migrate?

Here are the key reasons to use the new updated API provided by GroupDocs.Annotation for .NET since version 19.8:
*   **Annotator** class introduced as a **single entry point** to manage the document annotating process to any supported file format (instead of **AnnotationImageHandler** class from previous versions).
*   The overall **rendering speed improved** dramatically by saving rendered page as soon as it was rendered, not when all pages list were rendered.
*   Document **saving options simplified** so it’s easy to instantiate proper options class and control over document annotating and saving processes.

### How To Migrate?
Here is a brief comparison of how to annotate document and save it using old and new API.

#### Old coding style
```csharp
// Creating annotation list
List<AnnotationInfo> annotations = new List<AnnotationInfo>()
{
    new AnnotationInfo()
    {
        PageNumber = 0,
        Box = new Rectangle(100, 100, 100, 100),
        Type = Domain.AnnotationType.Area,
        Text = "area"
    },
                
    new AnnotationInfo()
    {
        PageNumber = 0,
        Box = new Rectangle(200, 200, 80, 80),
        Type = Domain.AnnotationType.Ellipse,
        Text = "ellipse"
    }
};

// Create annotation config
AnnotationConfig config = new AnnotationConfig();
// Set storage path
config.StoragePath = "storage";
// Create annotation handler
AnnotationImageHandler annotator = new AnnotationImageHandler(config);
// Create input file
using (FileStream fs = new FileStream("input.pdf", FileMode.Open))
{
    // Export annotations and save result
    Stream result = annotator.ExportAnnotationsToDocument(fs, annotations);
}
```

#### New coding style
```csharp
// Create list of annotations
List<AnnotationBase> annotations = new List<AnnotationBase>()
{
    new AreaAnnotation()
    {
        PageNumber = 0,
        Box = new Rectangle(100, 100, 100, 100),
        Message = "area"
    },
                
    new EllipseAnnotation()
        {
            PageNumber = 0,
            Box = new Rectangle(200, 200, 80, 80),
            Message = "ellipse"
        }
};

// Create annotator
using  (Annotator annotator = new Annotator("input.pdf"))
{
    // Add annotations
    annotator.Add(annotations);
    // Save result to "result.pdf"
    annotator.Save("result.pdf", new SaveOptions());
}
```
  
For more code examples and specific use cases please refer to our Developer Guide documentation or [GitHub](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET) samples and showcases.
