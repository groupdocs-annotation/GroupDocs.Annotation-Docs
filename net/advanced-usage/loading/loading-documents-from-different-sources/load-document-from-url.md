---
id: load-document-from-url
url: annotation/net/load-document-from-url
title: Load document from URL
weight: 3
description: "The article describes how to load PDF, Word, Excel, PowerPoint documents from URL using GroupDocs.Annotation for .NET."
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

The following example shows how to load a document using URL:

{{< tabs "example1">}}
{{< tab "C#" >}}
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
{{< /tab >}}
{{< /tabs >}}