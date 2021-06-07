---
id: extracting-image-from-image-annotation
url: annotation/net/extracting-image-from-image-annotation
title: Extracting image from image annotation
weight: 5
description: "Following this guide you will learn how to extract images from image annotations of document using GroupDocs.Annotation for .NET API."
keywords: Image, Extract Image, ImageAnnotation, Get Image, Extract Image from annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---

If you added any ImageAnnotation to file and saved it using [Annotator](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator), you can extract Image from ImageAnnotation using [ImageAnnotation.GetImage()](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/methods/getimage) method.

Here is the example of the code:

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
