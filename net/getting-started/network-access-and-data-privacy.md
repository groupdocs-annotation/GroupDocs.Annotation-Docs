---
id: network-access-and-data-privacy
url: annotation/net/network-access-and-data-privacy
title: Network access and data privacy
weight: 8
description: "Explains when GroupDocs.Annotation for .NET accesses the network, what data leaves your machine, how external resources referenced by documents are handled, and how to prevent outbound requests in air-gapped or security-sensitive deployments."
keywords: on-premise, offline, air-gapped, network access, data privacy, external resources, outbound requests, firewall, SSRF, SkipExternalResources
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: true
tags: csharp, annotation, network, security, privacy, air-gapped
---
## Summary

GroupDocs.Annotation for .NET is an **on-premise library**. It runs entirely inside your own process, on your own machine and network. It does not send your documents, your annotations, or any customer information to GroupDocs.

As stated in the [GroupDocs Customer Data and Security policy](https://about.groupdocs.com/security/customer-data-and-security/):

> GroupDocs products run on customer's own machines, infrastructure and network and do not send any files back to GroupDocs for processing and therefore does not have access to them.

"We never receive your data" and "the library never opens a socket" are two different statements. This topic describes every situation in which GroupDocs.Annotation can make an outbound request, so that you can audit and restrict them.

{{< alert style="info" >}}
**Short version.** GroupDocs.Annotation never transmits your document content anywhere. Starting with version **26.10**, it also does **not** retrieve the resources that a document refers to — remote images, style sheets, linked files — unless you allow them with [LoadOptions]({{< ref "annotation/net/advanced-usage/loading/load-external-resources.md" >}}).

The remaining outbound requests are all made because your code asked for them: an image annotation loaded from a URL, a license loaded from a URL, or a metered license.
{{< /alert >}}

## What never leaves your machine

Regardless of configuration, GroupDocs.Annotation does **not**:

* upload documents, document fragments, annotations, or rendered page previews to GroupDocs or any third party;
* transmit file names, file paths, or directory listings;
* collect telemetry, analytics, or usage statistics about the *content* of your documents.

This matches the [GroupDocs Terms of Use](https://about.groupdocs.com/legal/terms-of-use/):

> No information is collected by the product; technical information must be provided to GroupDocs by you through the support process.

{{< alert style="info" >}}
A file-based or stream-based license is validated entirely offline, in-process, and requires no connectivity at any point. A **metered** license is different: it reports usage volume to a billing endpoint, as described under *Metered licensing* below.
{{< /alert >}}

## When GroupDocs.Annotation accesses the network

There are four situations. The first one is driven by the content of a document and is **off by default** since version 26.10. The other three happen only because your code asked for them.

### 1. External resources referenced by a document — off by default

A document can reference a resource by an absolute URL:

* `<img src="http://…">` or `<link rel="stylesheet" href="http://…">` in an HTML file or in the HTML body of an e-mail message (EML, MSG, MHT);
* a linked (not embedded) picture or an `INCLUDEPICTURE` field in a Word processing document;
* a linked picture or media in a presentation;
* an external workbook link in a spreadsheet.

Since version **26.10**, GroupDocs.Annotation **skips** such resources in every operation — `Get`, `Add`, `Save`, `GeneratePreview` and `GetDocumentInfo`. No request is made; a skipped image is rendered as an empty (transparent) placeholder, and the link is kept in the saved document. Resources stored inside the document — `cid:` parts of an e-mail, `data:` URIs, embedded pictures — are always loaded.

{{< alert style="warning" >}}
**Versions before 26.10 load these resources by default and offer no switch to stop it.** If you process untrusted documents with an older version, upgrade, or block outbound traffic from the process as described in [Preventing outbound requests](#preventing-outbound-requests).
{{< /alert >}}

You can allow resources from trusted locations, or decide about every resource yourself, with three [LoadOptions](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/) members:

| Member | Default | Description |
| --- | --- | --- |
| [SkipExternalResources](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/skipexternalresources/) | `true` | Set it to `false` to load every external resource (the pre-26.10 behaviour). |
| [WhitelistedResources](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/whitelistedresources/) | empty | Host names or absolute URI prefixes that are loaded even when resources are skipped. |
| [ExternalResourceHandler](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.options/loadoptions/externalresourcehandler/) | `null` | Called for every external resource; it can allow it, skip it, or supply its content. |

See [Load external resources]({{< ref "annotation/net/advanced-usage/loading/load-external-resources.md" >}}) for examples.

{{< alert style="warning" >}}
**Why loading external resources is risky.** If you allow them for documents from outside your organisation, be aware of the consequences:

* **Server-Side Request Forgery (SSRF).** A crafted document can name an internal host — `http://169.254.169.254/`, `http://10.0.0.5:8080/` — and make your server request it from inside your network perimeter.
* **Credential leak.** A UNC path (`\\host\share\image.png`) can make Windows send the NTLM credentials of the process to that host.
* **Tracking pixels.** A remote image confirms to the sender that the document was processed, and reveals your server's public IP address.
* **Denial of service.** A document referencing a slow or unreachable host may stall processing.

Prefer `WhitelistedResources` or an `ExternalResourceHandler` allow-list over `SkipExternalResources = false`.
{{< /alert >}}

### 2. Images of image annotations — explicit

When you add an [ImageAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/imageannotation/) whose `ImagePath` is a URL, GroupDocs.Annotation downloads that image while saving the annotation:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    annotator.Add(new ImageAnnotation
    {
        Box = new Rectangle(100, 100, 100, 100),
        ImagePath = "https://example.com/stamp.png", // downloaded when the annotation is saved
        PageNumber = 0
    });
    annotator.Save("result.pdf");
}
```

The address comes from your code, so `LoadOptions` does not apply to it. The downloaded image is stored in the document: opening, previewing or re-saving an annotated document does not download it again.

{{< alert style="warning" >}}
If `ImagePath` is not an existing local file, GroupDocs.Annotation treats the value as a web address and also tries it with an `http://` and an `http://www.` prefix. A mistyped local path such as `stamp.png` therefore results in requests to the hosts `stamp.png` and `www.stamp.png`.

Use absolute local paths, check that the file exists before adding the annotation, or pass the image content in `ImageData` (Base64) — then no request is made. If the URL comes from untrusted input, validate it against an allow-list first: GroupDocs.Annotation does not restrict schemes, hosts, ports or private IP ranges on your behalf.
{{< /alert >}}

### 3. Setting a license from a URL — explicit

If the string you pass to `License.SetLicense(string)` is not an existing file and is an absolute URL, GroupDocs.Annotation downloads the license from that URL (with a 5-second timeout). Pass a local path or a `Stream` to avoid any request.

### 4. Metered licensing — explicit, opt-in

If — and only if — you activate a [metered license]({{< ref "annotation/net/getting-started/licensing-and-subscription.md" >}}) with `SetMeteredKey`, the library contacts the GroupDocs licensing and billing service. The key is validated over the network when you set it, and consumption data is uploaded on a recurring basis thereafter.

What is transmitted is **usage volume** — the quantity of operations performed and the total size of processed files — not document content and not customer data.

{{< alert style="warning" >}}
A metered license needs regular connectivity to report consumption. **A metered license is therefore unsuitable for air-gapped deployments** — use a file-based or stream-based license, which needs no connectivity at any point.
{{< /alert >}}

### Loading documents from remote storage

GroupDocs.Annotation does not download documents by itself. The [load from URL]({{< ref "annotation/net/advanced-usage/loading/loading-documents-from-different-sources/load-document-from-url.md" >}}), FTP, Amazon S3 and Azure Blob storage examples download the document in **your** code and pass a `Stream` to the `Annotator`. If your application does not do this, these connections do not occur.

<!-- Measured (format x API) table: add from the probe-harness run on 26.10.0 (ANNOTATIONNET-2663) before publishing. -->

## Preventing outbound requests

**Block egress at the network or process level.** Run the annotation component in a container, network namespace, VM, or subnet with no outbound route, or apply an outbound firewall rule to the process. This is the only control that covers every path, and the only one that cannot be bypassed by a defect. For an air-gapped deployment it is both necessary and sufficient.

Alongside it, reduce the surface in application code:

**1. Keep the default `SkipExternalResources = true`.** If you need resources from known locations, list them in `WhitelistedResources` rather than switching skipping off.

**2. Do not use URLs for `ImageAnnotation.ImagePath`.** Use an absolute local path or `ImageData`.

**3. Download documents yourself.** If your application must accept URLs, download them in your own code where you can apply your own validation and timeout, then pass the resulting `Stream` to the `Annotator`.

**4. Use a file-based or stream-based license, not a metered license**, and load it from a local path or a stream.

## Diagnosing unexpected HTTP requests

If you observe outbound HTTP traffic from an application that uses GroupDocs.Annotation and want to determine whether the library is responsible:

1. **Capture the requests** with Fiddler, Wireshark, or a logging proxy, and record the destination URLs.
2. **Compare them against your input documents.** If a captured URL appears verbatim inside a document — as an `<img>` source, a stylesheet `href`, a linked picture — check whether `SkipExternalResources` is set to `false` or the host is listed in `WhitelistedResources`.
3. **Compare them against your code.** Check the `ImagePath` values of image annotations, including paths that do not exist on disk, and the license path.
4. **Check the destinations against the licensing service** if you use a metered license. Those requests are unrelated to the documents being processed.

{{< alert style="info" >}}
An `ExternalResourceHandler` that only logs `args.Uri` and leaves `args.Skipped` unchanged is a simple way to see every external resource a document references, without changing what is loaded.
{{< /alert >}}

## More resources

### Advanced usage topics

To learn more about the features mentioned above, please refer to the following articles:

*   [Load external resources]({{< ref "annotation/net/advanced-usage/loading/load-external-resources.md" >}})
*   [Load document from URL]({{< ref "annotation/net/advanced-usage/loading/loading-documents-from-different-sources/load-document-from-url.md" >}})
*   [Load document from stream]({{< ref "annotation/net/advanced-usage/loading/loading-documents-from-different-sources/load-document-from-stream.md" >}})
*   [Licensing and subscription]({{< ref "annotation/net/getting-started/licensing-and-subscription.md" >}})
*   [GroupDocs Customer Data and Security](https://about.groupdocs.com/security/customer-data-and-security/)

### GitHub examples

You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Annotation for .NET examples](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)

### Free online document annotation App

Along with the full-featured .NET library we provide a simple but powerful free App.

You are welcome to annotate PDF, DOC, DOCX, PPT, PPTX, XLS, XLSX and other documents with our [Free Online Document Annotation App](https://products.groupdocs.app/annotation).
