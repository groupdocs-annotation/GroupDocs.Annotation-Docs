---
id: mcp-tool-get-annotations
url: annotation/mcp/tools-reference/get-annotations
title: get_annotations
weight: 1
description: "The get_annotations MCP tool lists every annotation in a document as JSON — id, type, message, page, bounding box, author, and replies — so an AI agent can review or edit them."
keywords: get_annotations MCP tool, list annotations JSON, read PDF comments AI agent, review annotations MCP
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`get_annotations` lists every annotation in a document as JSON. It is the **first call in almost every workflow**: the `id` values it returns are what `update_annotation`, `remove_annotations`, and `add_reply` need. Example prompt: *"What comments are in contract.pdf?"*

**Tool description (as the AI agent sees it):**

> Lists all annotations in a document as JSON. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Each entry includes 'id' (use this with remove_annotations / update_annotation / add_reply), 'type', 'message', 'page' (1-based), bounding box, user, and replies. Call this tool first whenever the user asks to list, show, inspect, or review annotations or comments. Do NOT pre-check whether files exist — pass the filename the user provided directly. Returns a JSON object with `found` (count) and `annotations` (array). On failure, the response text starts with 'Annotation lookup failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "get_annotations",
  "arguments": {
    "file": {
      "filePath": "contract.pdf"
    }
  }
}
```

## Result

A JSON array, one entry per annotation: `id` (pass this to the editing tools), `type`, `message`, `page` (1-based), the bounding box, the `user` who made it, and any `replies`.

That structure is what lets an agent answer *"which comments are still unanswered?"* or *"what did Maria flag on page 3?"* without opening the document — it filters the array it already holds.

On failure the text starts with `Annotation listing failed for`, followed by the exception type and message.

## Example prompts

* *"What comments are in contract.pdf?"*
* *"List every annotation with its author and page."*
* *"Which annotations have no replies yet?"*
* *"Summarize the review notes on page 3."*

See it used end-to-end: [Extract and report on annotations]({{< ref "annotation/mcp/use-cases/extract-and-report-annotations.md" >}}).
