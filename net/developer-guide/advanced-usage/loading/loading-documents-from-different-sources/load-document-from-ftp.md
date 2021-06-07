---
id: load-document-from-ftp
url: annotation/net/load-document-from-ftp
title: Load document from FTP
weight: 4
description: "This article explains how to load PDF, Word, Excel, PowerPoint documents from FTP when using GroupDocs.Annotation for .NET."
keywords: Load document from URL, Load document by FTP GroupDocs.Annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
Following example demonstrates how to annotate document from FTP.

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
