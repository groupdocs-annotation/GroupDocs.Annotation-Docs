---
id: load-document-from-url
url: annotation/net/load-document-from-url
title: Load document from URL
weight: 3
description: "This article explains how to load PDF, Word, Excel, PowerPoint documents from URL when using GroupDocs.Annotation for .NET."
keywords: Load document from URL, Load document by URL GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to load document from Url
        description: Learn how to load document from Url step by step
        steps:
        - name: Get file stream
          text: Create a method that will receive the document stream.
        - name: Get response
          text: Create a method that will receive the response.
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass method and Url to it. You may specify absolute or relative file path as per your requirements.
        - name: Annotation class declaration
          text: Create an instance of annotation class.
        - name: Specify annotation options 
          text: In the annotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name annotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file with class SaveOptions.
toc: True
---

Following example demonstrates how to annotate document from URL.

```csharp
string url = "https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/blob/master/Examples/Resources/SampleFiles/input.pdf?raw=true";


using (Annotator annotator = new Annotator(GetRemoteFile(url)))
{
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
	annotator.Save("result.pdf");
}

private static Stream GetRemoteFile(string url)
{
	WebRequest request = WebRequest.Create(url);
	using (WebResponse response = request.GetResponse())
		return GetFileStream(response);
}

private static Stream GetFileStream(WebResponse response)
{
	MemoryStream fileStream = new MemoryStream();
	using (Stream responseStream = response.GetResponseStream())
		responseStream.CopyTo(fileStream);
		fileStream.Position = 0;
		return fileStream;
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
