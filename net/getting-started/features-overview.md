---
id: features-overview
url: annotation/net/features-overview
title: Features Overview
weight: 1
description: Variety of features to manipulate graphics, watermarks and text annotations
keywords: text annotations, watermark, annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---
## Adding, editing, and removing annotations

GroupDocs.Annotation for .NET main feature is document annotation that supports over 13 different annotation types for over 35 file formats.

You can use various graphic, text, and watermark annotation types. See available annotation types in the list below.

### Graphic annotations

*   Area marks an area with a rectangle and adds notes to it
*   Arrow draws an arrow in a document
*   Distance measures the distance between objects in a document
*   Point sticks comments to any point in a document
*   Polyline draws shapes and freehand lines
*   Redaction fills the black rectangle with a fixed position (use if you want to hide some text)
*   Text field adds a rectangle with text inside
*   Ellipse draws elliptic annotation in a document

### Text annotations

*   Highlight highlights and comments selected text
*   Replacement replaces the original text with the user’s text
*   Strikeout marks text with a strike-through styling
*   Underline marks text with an underline styling

### Watermark annotations

*   Horizontal adds horizontal text watermark
*   Diagonal adds diagonal text watermark

## Import annotations

GroupDocs.Annotation for .NET provides the ability to work with annotations added by other software.

## Adding and removing comments

Each annotation type supports comment collaboration. Add, remove, or reply to comments for any annotation.

## Export of annotated document

GroupDocs.Annotation for .NET saves the annotated document in the origin format for most supported file types. For details, see [list of supported formats]({{< ref "annotation/net/getting-started/supported-document-formats.md" >}})

## Generation of document pages previews & thumbnails

GroupDocs.Annotation for .NET allows you to render document pages as images for your desktop, mobile, or web front-end applications. You can view any document, calculate the annotation coordinates more precisely, or generate a preview or thumbnails.

## Caching results

By default, GroupDocs.Annotation stores the cache on a local disk. 
Nevertheless, however GroupDocs.Annotation allows you to use a custom cache by implementing appropriate interfaces such as Amazon S3, Dropbox, Google Drive, Windows Azure, Redis, or others.
