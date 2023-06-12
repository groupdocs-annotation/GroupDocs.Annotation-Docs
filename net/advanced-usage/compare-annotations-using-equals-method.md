---
id: comparing-annotations-using-equals-method
url: annotation/net/comparing-annotations-using-equals-method
title: Compare annotations
weight: 6
description: "The page describes how to compare annotations."
keywords: compare, annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to compare annotation using equals method
        description: Learn how to compare annotation using equals method step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements.
        - name: Get annotation
          text: Get all annotations to created variable.
        - name: Annotation class declaration          
          text: Create an instance of ImageAnnotation class.
        - name: Specify annotation options 
          text: In the ImageAnnotation class constructor, pass parameters.
        - name: Compare annotations
          text: With a foreach loop, compare all annotations with yours.
toc: True
---

You have the ability to compare annotations using the [Equals](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/equals) method or the already implemented [IEquatable](https://docs.microsoft.com/en-us/dotnet/api/system.iequatable-1) interface.

The following code snippet shows how to compare annotations:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("annotated_file.pdf"))
{
	var annotations = annotator.Get();
	ImageAnnotation imageAnnotation = new ImageAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		Opacity = 0.7,
		PageNumber = 0,
		ImagePath = "www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png",
		Angle = 100
	};
	foreach (var annotation in annotations)
	{
		if (imageAnnotation.Equals(annotation))
		{
			// Do some stuff here...
		}
	}
}
```
{{< /tab >}}
{{< /tabs >}}
