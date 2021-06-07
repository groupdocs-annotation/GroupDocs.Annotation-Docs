---
id: load-document-from-azure-blob-storage
url: annotation/net/load-document-from-azure-blob-storage
title: Load document from Azure Blob Storage
weight: 6
description: "This article explains how to load PDF, Word, Excel, PowerPoint documents from Azure Blob storage storage when using GroupDocs.Annotation for .NET."
keywords: Load document from URL, Load document from Azure Blob storage by GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
Following example demonstrates how to annotate document from Azure Blob Storage.

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

{{< alert style="info" >}}NOTE: Package WindowsAzure.Storage version 9.3.3 should be referenced{{< /alert >}}

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