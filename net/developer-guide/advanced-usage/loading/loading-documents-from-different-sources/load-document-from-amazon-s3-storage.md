---
id: load-document-from-amazon-s3-storage
url: annotation/net/load-document-from-amazon-s3-storage
title: Load document from Amazon S3 Storage
weight: 5
description: "This article explains how to load PDF, Word, Excel, PowerPoint documents from Amazon S3 storage when using GroupDocs.Annotation for .NET."
keywords: Load document from URL, Load document from Amazon S3 storage GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
Following example demonstrates how to annotate document from Amazon S3 Storage.

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

{{< alert style="info" >}}NOTE: Packages AWSSDK.S3 version 3.3.104.30 and AWSSDK.Core version 3.3.103.42 should be referenced{{< /alert >}}

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