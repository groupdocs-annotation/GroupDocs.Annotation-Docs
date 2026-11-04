---
id: load-external-resources
url: annotation/net/load-external-resources
title: Load external resources
weight: 3
description: "The page describes how GroupDocs.Annotation for .NET handles images, style sheets and other resources that a document references by URL, and how to skip, allow or substitute them with LoadOptions."
keywords: external resources, remote images, SkipExternalResources, WhitelistedResources, ExternalResourceHandler, SSRF, offline
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to control external resources of a document
        description: Learn how to skip, allow or substitute external resources step by step
        steps:
        - name: Create load options
          text: Create an instance of LoadOptions and set SkipExternalResources, WhitelistedResources or ExternalResourceHandler.
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass the file path and the load options to it.
        - name: Process the document
          text: Generate a preview, add annotations or save the document as usual.
toc: True
---

A document can reference resources that are stored outside of it, for example:

* an `<img src="https://...">` in an HTML page or in the body of an e-mail message;
* a linked (not embedded) picture in a Word document;
* a remote style sheet;
* an external workbook link.

Starting with version 26.10, [GroupDocs.Annotation](https://products.groupdocs.com/annotation/net) **does not load such resources by default**. Opening, previewing or saving a document makes no network or file-share request for the resources the document references. A skipped image is rendered as an empty (transparent) placeholder, and the link itself is kept, so a saved document still references the original resource.

Resources stored inside the document are always loaded: `cid:` parts of an e-mail message, `data:` URIs and embedded pictures.

The behaviour is controlled by three members of the [LoadOptions](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/) class:

| Member | Default | Description |
| --- | --- | --- |
| [SkipExternalResources](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/skipexternalresources/) | `true` | Skip the external resources referenced by the document. Set it to `false` to load them all. |
| [WhitelistedResources](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/whitelistedresources/) | empty | Resources that are loaded even when `SkipExternalResources` is `true`. Each entry is a host name or an absolute URI prefix. |
| [ExternalResourceHandler](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/externalresourcehandler/) | `null` | Called for every external resource before it is loaded. It can allow the resource, skip it, or supply its content. |

The options apply to every operation: `Get`, `Add`, `Save`, `GeneratePreview` and `GetDocumentInfo`, for Word processing, HTML, e-mail (EML, MSG, MHT), presentation and spreadsheet documents.

{{< alert style="info" >}}
Images of an [ImageAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/) are not covered by these options: `ImagePath` is a resource that your code specifies, not one that the document references. See [Network access and data privacy]({{< ref "annotation/net/getting-started/network-access-and-data-privacy.md" >}}) for details.
{{< /alert >}}

## Skip external resources (default)

No code is needed: external resources are skipped unless you allow them. The following example generates a preview of a Word document with linked pictures without loading them:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("remote-resources.docx"))
{
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
        File.Create($"result_{pageNumber}.png"));
    previewOptions.PreviewFormat = PreviewFormats.PNG;

    annotator.Document.GeneratePreview(previewOptions); // linked pictures are rendered as empty placeholders
}
```
{{< /tab >}}
{{< /tabs >}}

## Allow trusted locations only

Add the trusted locations to `WhitelistedResources`. `SkipExternalResources` stays `true`, so everything else is still skipped. An entry matches as follows:

* **Host name**, for example `"example.com"`: matches that host and its subdomains.
* **Absolute URI prefix**, for example `"https://cdn.example.com/images/"`: the scheme, host and port must match exactly, and the path matches only on a segment boundary, so `/images` admits `/images/x.png` but not `/images-private/x.png`.

{{< tabs "example2">}}
{{< tab "C#" >}}
```csharp
LoadOptions loadOptions = new LoadOptions
{
    WhitelistedResources = new List<string> { "cdn.example.com", "https://intranet.example.com/images/" }
};

using (Annotator annotator = new Annotator("input.html", loadOptions))
{
    annotator.Save("result.html"); // only resources from the two trusted locations are loaded
}
```
{{< /tab >}}
{{< /tabs >}}

## Inspect, allow or substitute each resource

Derive a class from [ExternalResourceHandler](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/externalresourcehandler/) and override [OnLoading](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/externalresourcehandler/onloading/). The handler is called for every external resource. [ExternalResourceLoadingArgs](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/externalresourceloadingargs/) provides:

* `Uri` - the resource address as written in the document;
* `Skipped` - pre-set from `SkipExternalResources` and `WhitelistedResources`; set it to `true` to skip the resource or to `false` to load it;
* `Data` - set it to supply the resource content yourself; nothing is requested then.

The following example serves a local copy of a picture instead of downloading it, and skips everything else:

{{< tabs "example3">}}
{{< tab "C#" >}}
```csharp
class LocalCopyResourceHandler : ExternalResourceHandler
{
    public override void OnLoading(ExternalResourceLoadingArgs args)
    {
        if (args.Uri == "https://example.com/images/banner.png")
            args.Data = File.ReadAllBytes("banner.png"); // served locally, nothing is requested
        else
            args.Skipped = true;
    }
}

LoadOptions loadOptions = new LoadOptions { ExternalResourceHandler = new LocalCopyResourceHandler() };

using (Annotator annotator = new Annotator("remote-resources.docx", loadOptions))
{
    annotator.Document.GeneratePreview(new PreviewOptions(pageNumber => File.Create($"result_{pageNumber}.png")));
}
```
{{< /tab >}}
{{< /tabs >}}

{{< alert style="info" >}}
Prefer an allow-list over a deny-list. Blocking an address such as `http://169.254.169.254/` by pattern is fragile: DNS names, redirects, IPv6 literals and decimal-encoded IP addresses all defeat naive filtering.
{{< /alert >}}

## Load all external resources

Set `SkipExternalResources` to `false` to restore the behaviour of versions before 26.10. Do this only for documents you trust: a document from an untrusted source can make your server request internal addresses (server-side request forgery), and a UNC path can expose the Windows credentials of the process.

{{< tabs "example4">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.eml", new LoadOptions { SkipExternalResources = false }))
{
    annotator.Save("result.eml");
}
```
{{< /tab >}}
{{< /tabs >}}

## More resources

### Advanced usage topics

* [Network access and data privacy]({{< ref "annotation/net/getting-started/network-access-and-data-privacy.md" >}})
* [Load the password-protected documents]({{< ref "annotation/net/advanced-usage/loading/load-password-protected-documents.md" >}})

### GitHub examples

You may easily run the code above and see the feature in action in our GitHub examples:

* [GroupDocs.Annotation for .NET examples](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
