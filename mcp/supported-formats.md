---
id: mcp-supported-formats
url: annotation/mcp/supported-formats
title: Supported formats
weight: 4
description: "The MCP server exposes the full GroupDocs.Annotation engine: every format the .NET library can annotate — PDF, Word, Excel, PowerPoint, images, CAD, email and 50+ more — is available to your AI agent."
keywords: MCP server supported formats, annotate pdf MCP, annotate docx MCP, annotate images MCP, supported annotation formats
productName: GroupDocs.Annotation MCP Server
toc: True
---

The MCP server exposes the **full GroupDocs.Annotation engine**: every format the .NET library can annotate — 50+ document, spreadsheet, presentation, image, CAD, email, and web formats — is available to your AI agent through the annotation tools. The canonical matrix lives in the library documentation: [supported document formats]({{< ref "annotation/net/getting-started/supported-document-formats.md" >}}).

What agents are asked for most:

* **PDF** — the default review format: highlights, comments, strikeouts, and threads that any PDF reader will show.
* **DOCX / DOC** — mark up a draft without converting it first.
* **XLSX** — annotate figures in place, on the sheet where they live.
* **PPTX** — comment on slides during a deck review.
* **Images (PNG, JPG, TIFF)** — `area`, `point`, and `arrow` annotations work on scans and screenshots too.

**Annotation types** are the same across formats: `textfield`, `area`, `point`, `arrow`, `highlight`, `underline`, `strikeout`. Text-anchored types (`highlight`, `underline`, `strikeout`) need a text layer — on a scanned image, use `area` or `arrow` instead.

Not sure what you are holding, or how big its pages are? Ask — *"what format is this and how many pages?"* — and the agent answers via [`get_document_info`]({{< ref "annotation/mcp/tools-reference/get-document-info.md" >}}).
