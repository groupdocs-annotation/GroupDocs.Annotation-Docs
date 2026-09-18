---
id: mcp-tool-get-document-info
url: annotation/mcp/tools-reference/get-document-info
title: get_document_info
weight: 10
description: "The get_document_info MCP tool returns file type, page count, size, and per-page dimensions for a document — without annotating it."
keywords: get_document_info MCP, MCP document info tool, page count before annotating, ai agent inspect document
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`get_document_info` returns the file type, page count, size, and per-page dimensions — without touching the annotations. Agents use it to check page numbers before annotating and to size coordinates sensibly. Example prompt: *"How many pages is this, and how big is page 1?"*

**Tool description (as the AI agent sees it):**

> Returns file type, page count, size, and per-page dimensions for a document as JSON. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Call this tool whenever the user asks for document info, page count, size, dimensions, or wants to inspect a document before annotating. Do NOT pre-check whether files exist — pass the filename the user provided directly. Returns a JSON object with `fileType`, `pageCount`, `size`, and `pages` (array of per-page width/height when available). On failure, the response text starts with 'Document-info lookup failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "get_document_info",
  "arguments": {
    "file": {
      "filePath": "contract.pdf"
    }
  }
}
```

## Result

A JSON object with `fileName`, `fileType`, `pageCount`, `sizeBytes`, and `pages` — width and height per page.

Per-page dimensions matter more here than in other servers: `x`/`y` on `add_annotation` are document coordinates, so knowing the page box is what keeps an annotation on the page.

On failure the text starts with `Document-info lookup failed for`, followed by the exception type and message.

## Example prompts

* *"How many pages does contract.pdf have?"*
* *"What are the page dimensions — I want to place a note in the top-right corner."*
* *"Is this a PDF or a Word file?"*
