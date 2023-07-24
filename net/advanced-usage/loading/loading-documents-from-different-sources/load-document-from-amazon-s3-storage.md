---
id: load-document-from-amazon-s3-storage
url: annotation/net/load-document-from-amazon-s3-storage
title: Load document from Amazon S3 Storage
weight: 5
description: "The page describes how to load PDF, Word, Excel, PowerPoint documents from Amazon S3 storage when using GroupDocs.Annotation for .NET."
keywords: Load document from URL, Load document from Amazon S3 storage GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: GroupDocs Annotation
        discription: Represent text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
        showVideo: False
        howTo:
           name: How to load document from amazon
           description: Learn how to add document from amazon step by step
           steps:
           - name: Load document from amazon
             text: Create a method that will receive the document stream from amazon.
           - name: Load source fule an instance Annotator
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

The following code snippet shows how to load a document from Amazon S3 Storage:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
string key = "sample.pdf";
using (Annotator annotator = new Annotator(DownloadFile(key)))
{
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
	annotator.Save("result.pdf");
}

private static Stream DownloadFile(string key)
{
	AmazonS3Client client = new AmazonS3Client();
	string bucketName = "my-bucket";
	GetObjectRequest request = new GetObjectRequest
	{
		Key = key,
		BucketName = bucketName
	};
	using (GetObjectResponse response = client.GetObject(request))
	{
		MemoryStream stream = new MemoryStream();
		response.ResponseStream.CopyTo(stream);
		stream.Position = 0;
		return stream;
	}
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}NOTE: Packages AWSSDK.S3 version 3.3.104.30 and AWSSDK.Core version 3.3.103.42 should be referenced{{< /alert >}}