---
id: mcp-tool-generate-pages-preview
url: annotation/mcp/tools-reference/generate-pages-preview
title: generate_pages_preview
weight: 9
description: "The generate_pages_preview MCP tool renders document pages as PNG images and returns them inline, so an AI client can display and the agent can see the annotated page."
keywords: generate_pages_preview MCP tool, render document page PNG AI, show document to agent, inline image MCP tool
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`generate_pages_preview` renders pages as **PNG images returned inline** — with annotations baked in — so a client that supports image content can show them, and the agent can look at what it just did. Pass `pages` as `1,3,5` or `1-3`; omit it for page 1. Example prompt: *"Show me page 2 with the highlight"*.

**Tool description (as the AI agent sees it):**

> Renders document pages as PNG images and returns them inline so AI clients can display them directly. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Pass 'pages' as a comma-separated list (e.g. '1,3,5') or a range ('1-3'); omit to render only page 1. Renders the document with its annotations baked in — call this whenever the user asks to preview, show, render, or visualise a page (annotated or not). Maximum MaxPagesPerCall (5) pages per call; further pages must be requested in additional calls. Do NOT pre-check whether files exist — pass the filename the user provided directly. Returns a CallToolResult with one TextContentBlock describing what was rendered, followed by one ImageContentBlock per page. On failure, the response contains a single TextContentBlock starting with 'Preview generation failed for'.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `pages` | string | no | Pages to render, e.g. '1,3,5' or '1-3'. Omit for page 1 only. |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "generate_pages_preview",
  "arguments": {
    "file": {
      "filePath": "contract_annotated.pdf"
    },
    "pages": "1-3"
  }
}
```

## Result

One text block describing what was rendered, followed by **one image block per page**.

This is the tool that closes the loop on annotation work: the agent adds a highlight, renders the page, and can verify the placement rather than asserting it. Rendering is the most expensive call in this server — ask for the pages you need, not the whole document.

On failure a single text block starts with `Preview generation failed for`.

## Example prompts

* *"Show me page 2 with the highlight you just added."*
* *"Render pages 1-3 so I can check the annotations."*
* *"Preview the first page of the annotated contract."*

See it used end-to-end: [Let the agent see the page]({{< ref "annotation/mcp/use-cases/visual-preview-for-agents.md" >}}).
