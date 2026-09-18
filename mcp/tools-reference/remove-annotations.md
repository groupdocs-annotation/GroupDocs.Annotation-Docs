---
id: mcp-tool-remove-annotations
url: annotation/mcp/tools-reference/remove-annotations
title: remove_annotations
weight: 4
description: "The remove_annotations MCP tool removes annotations from a document by ID, or clears every annotation at once."
keywords: remove_annotations MCP tool, delete annotations PDF AI, clear comments document MCP, strip annotations before sharing
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`remove_annotations` deletes annotations by ID — or every annotation in the document when `ids` is omitted. The common use is producing a clean copy to send outside the review circle. Example prompt: *"Remove all annotations and give me a clean copy"*.

**Tool description (as the AI agent sees it):**

> Removes annotations from a document by ID and saves the result back to storage. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Call get_annotations first to retrieve annotation IDs, then pass them here. Omit 'ids' to remove every annotation in the document. Call this tool whenever the user asks to delete, remove, or clear annotations. Do NOT pre-check whether files exist — pass the filename the user provided directly. Returns a saved-path message ('Removed N annotation(s) from <file>'). On failure, the response text starts with 'Annotation removal failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `ids` | string | no | Comma-separated annotation IDs to remove, e.g. '1,3,5'. Omit to remove all. |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "remove_annotations",
  "arguments": {
    "file": {
      "filePath": "contract_annotated.pdf"
    },
    "ids": "3,7"
  }
}
```

## Result

A message naming the saved document and how many annotations were removed.

Omitting `ids` clears **everything** — which is exactly what you want before sending a document to a counterparty, and exactly what you do not want in the middle of a review. Ask the agent to confirm the count first.

On failure the text starts with `Annotation removal failed for`, followed by the exception type and message.

## Example prompts

* *"Remove all annotations and give me a clean copy to send."*
* *"Delete comments 3 and 7 — they are resolved."*
* *"Strip the internal review notes but keep the client's comments."*
