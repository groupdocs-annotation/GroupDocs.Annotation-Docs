---
id: extracting-image-from-image-annotation
url: annotation/net/extracting-image-from-image-annotation
title: Extract an image from an image annotation
weight: 5
description: "The page describes how to extract image from image annotation."
keywords: image, extract, ImageAnnotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to extracting image from image annotation
        description: Learn how to extracting image from image annotation step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Annotation collection
          text: Assign collection of annotations to all annotations
        - name: Check all annotations
          text: Сall a for loop and check all annotations in it
        - name: Save image
          text: Using the Image class, call the .Save() method
toc: True
---

You can extract an image from the [ImageAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/) object. To do this, call the [ImageAnnotation.GetImage()](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/methods/getimage) method.

The following code snippet shows how to extract an image from an image annotation:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("annotated_file.docx"))
{
	List<AnnotationBase> annotations = annotator.Get();
	for (int i = 0; i < annotations.Count; i++)
	{
		if (annotations[i] is ImageAnnotation imageAnnotation)
		{
			Image image = imageAnnotation.GetImage();
			image.Save($"extracted_image{i + 1}.{imageAnnotation.ImageExtension}");
		}
	}
}
```
{{< /tab >}}
{{< /tabs >}}
