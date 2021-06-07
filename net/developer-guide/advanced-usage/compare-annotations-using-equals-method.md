---
id: comparing-annotations-using-equals-method
url: annotation/net/comparing-annotations-using-equals-method
title: Comparing annotations using the equals method
weight: 6
description: "Following this guide you will learn how to compare annotations using equals method of document using GroupDocs.Annotation for .NET API."
keywords: Equals, Compare, Annotation, Annotations, Comparing, Compare annotations, IEquatable
productName: GroupDocs.Annotation for .NET
hideChildren: False
---

You have the ability to compare annotations using the [Equals]() method or the already implemented [IEquatable](https://docs.microsoft.com/en-us/dotnet/api/system.iequatable-1) interface.

Here is the example of the code:

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
