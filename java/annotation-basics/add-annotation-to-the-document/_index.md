---
id: add-annotation-to-the-document
url: annotation/java/add-annotation-to-the-document
title: Add annotation to the document
weight: 3
description: "The page describes document annotations of different types and how to  add annotations to a document using GroupDocs.Annotation API."
keywords: annotation, document, add
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
toc: True
---
## What is a document annotation?

Annotation is a textual or graphic notes, comments and remarks attached to a specific part of a document content - sections, paragraphs, sentences or even words. Annotations are often used by a group of collaborators to edit and review documents in a quick and handy manner - the document is shared with reviewers who then mark it up and add notes. Then assigned team members read these annotations and modify document content accordingly.

Today annotations can be programmatically added to a documents and images of various  types - PDF, Microsoft Word and Open Document text documents, Microsoft Excel spreadsheets, Microsoft PowerPoint presentations, PNG / JPG / TIFF images etc. 

  

### Add annotation to the document

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/java) allows you to apply various annotation types to the different document formats. Supported annotations list is described in a table below. 

### List of supported annotations

| Annotation | Description |
| --- | --- |
| [Area]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-area-annotation.md" >}}) | Rectangle annotation that can be applied in random place on document page. |
| [Arrow]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-arrow-annotation.md" >}}) | Annotation in the form of pointer or arrow. |
| [Distance]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-distance-annotation.md" >}}) | Annotation looks like arrow but with arrows at both line ends. For most document formats this annotation can contains text value (this feature not support for Word documents). |
| [Ellipse]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-ellipse-annotation.md" >}}) | Circle-based annotation. |
| [Link]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-link-annotation.md" >}}) | Represents a web-link that can be applied to the part of text. This annotation supports only for PDF, Word processing text documents and presentations. |
| [Point]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-point-annotation.md" >}}) | Represents abstract point annotation. |
| [Polyline]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-polyline-annotation.md" >}}) | Represents free-hand drawing line. |
| [Resource redaction]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-resource-redaction-annotation.md" >}}) | Represents free rectangle annotation with fixed position and black background. For this annotation is impossible to move it (in result document), and change any visual properties. |
| [Search text]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-text-search-annotation.md" >}}) | This annotation highlight search text. Applicable only for text. |
| [Squiggly]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-squiggly-annotation.md" >}}) | This annotation squiggly underline text. Applicable only for text. |
| [Text field]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-text-field-annotation.md" >}}) | This is a rectangle annotation with some text inside rectangle area. |
| [Highlight]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-highlight-annotation.md" >}}) | This annotation highlight text. Applicable only for text. |
| [Text redaction]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-text-redaction-annotation.md" >}}) | Same as resource redaction annotation, but applicable only for text. |
| [Replacement]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-replacement-annotation.md" >}}) | Replace original document text by user text. Applicable only for text. |
| [Strikeout]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-strikeout-annotation.md" >}}) | Make selected text strikeout. Applicable only for text. |
| [Underline]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-underline-annotation.md" >}}) | Make selected text underline. Applicable only for text. |
| [Watermark]({{< ref "annotation/java/annotation-basics/add-annotation-to-the-document/add-watermark-annotation.md" >}}) | Add text watermark. PageNumber for this annotation is ignored, because annotation adds to all document pages. For some document formats can set Angle property, that determines annotation angle rotation. |

For detailed explanation about how to apply different annotation types to a document, please check these guides:
