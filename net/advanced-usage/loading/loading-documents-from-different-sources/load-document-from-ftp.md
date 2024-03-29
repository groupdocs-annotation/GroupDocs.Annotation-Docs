---
id: load-document-from-ftp
url: annotation/net/load-document-from-ftp
title: Load document from FTP
weight: 4
description: "The page describes how to load PDF, Word, Excel, PowerPoint documents from FTP using GroupDocs.Annotation for .NET."
keywords: Load document from URL, Load document by FTP GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to load document from ftp
        description: Learn how to load document from ftp step by step
        steps:
        - name: Ftp web request
          text: Create a method that will create a request and pass the uniform resource identifier class to it.
        - name: Get file stream
          text: Create a method that will receive the file stream of the document and pass the web response class to it.
        - name: Load document from Ftp
          text: Create a method that will receive a file from ftp and pass the file path to it
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass method and source file path as a constructor parameter. 
        - name: Annotation class declaration
          text: Create an instance of AreaAnnotation class.
        - name: Specify annotation options 
          text: In the AreaAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name AreaAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---

The following code snippet shows how to annotate document from FTP:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator(GetFileFromFtp("sample.pdf")))
{
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
	annotator.Save("result.pdf");
}

private static Stream GetFileFromFtp(string filePath)
{
	Uri uri = new Uri(filePath);
	FtpWebRequest request = CreateRequest(uri);
	using (WebResponse response = request.GetResponse())
                return GetFileStream(response);
}

private static FtpWebRequest CreateRequest(Uri uri)
{
	FtpWebRequest request = (FtpWebRequest)WebRequest.Create(uri);
	request.Method = WebRequestMethods.Ftp.DownloadFile;
		return request;
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