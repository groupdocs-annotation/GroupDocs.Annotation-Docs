---
id: load-document-from-azure-blob-storage
url: annotation/net/load-document-from-azure-blob-storage
title: Load document from Azure Blob Storage
weight: 6
description: "The page describes how to load PDF, Word, Excel, PowerPoint documents from Azure Blob storage when using GroupDocs.Annotation for .NET."
keywords: Load document from URL, Load document from Azure Blob storage by GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to load document from azure
        description: Learn how to load document from azure step by step
        steps:
        - name: Get a cloud storage container
          text: Сreate a method that will receive the cloud storage object container
        - name: Load document from azure
          text: Сreate a method that will receive the document stream from azure.
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

The following code snippet shows how to load a document from Azure Blob Storage.

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
string blobName = "sample.pdf";
using (Annotator annotator = new Annotator(DownloadFile(blobName)))
{
	AreaAnnotation area = new AreaAnnotation()
	{
		Box = new Rectangle(100, 100, 100, 100),
		BackgroundColor = 65535,
	};
	annotator.Add(area);
	annotator.Save("result.pdf");
}

public static Stream DownloadFile(string blobName)
{
	CloudBlobContainer container = GetContainer();
	CloudBlob blob = container.GetBlobReference(blobName);
	MemoryStream memoryStream = new MemoryStream();
	blob.DownloadToStream(memoryStream);
	memoryStream.Position = 0;
	return memoryStream;
}

private static CloudBlobContainer GetContainer()
{
	string accountName = "***";
	string accountKey = "***";
	string endpoint = $"https://{accountName}.blob.core.windows.net/";
	string containerName = "***";
	StorageCredentials storageCredentials = new StorageCredentials(accountName, accountKey);
	CloudStorageAccount cloudStorageAccount = new CloudStorageAccount(
		storageCredentials, new Uri(endpoint), null, null, null);
	CloudBlobClient cloudBlobClient = cloudStorageAccount.CreateCloudBlobClient();
	CloudBlobContainer container = cloudBlobClient.GetContainerReference(containerName);
	container.CreateIfNotExists();
	return container;
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}NOTE: Package WindowsAzure.Storage version 9.3.3 should be referenced{{< /alert >}}