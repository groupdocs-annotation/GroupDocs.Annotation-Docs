---
id: mcp-tool-update-annotation
url: annotation/mcp/tools-reference/update-annotation
title: update_annotation
weight: 3
description: "The update_annotation MCP tool edits an existing annotation's message or bounding box in place and saves the result."
keywords: update_annotation MCP tool, edit annotation AI agent, move annotation MCP, change comment text document
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`update_annotation` edits an existing annotation: its message, its position, its size, or any combination. Omitted parameters keep their current value. Get the `id` from [`get_annotations`]({{< ref "annotation/mcp/tools-reference/get-annotations.md" >}}) first. Example prompt: *"Reword comment 3 to mention the new deadline"*.

**Tool description (as the AI agent sees it):**

> Updates an existing annotation's message and/or bounding box, then saves the result back to storage. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Call get_annotations first to retrieve the annotation 'id' and current values. Pass any subset of message/x/y/width/height — omitted parameters keep their current value. Call this tool whenever the user asks to edit, modify, move, or resize an existing annotation. Do NOT pre-check whether files exist — pass the filename the user provided directly. Returns a saved-path message ('Updated annotation <id> in <file>'). On failure, the response text starts with 'Annotation update failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `id` | integer | yes | Annotation ID to update (from get_annotations) |
| `message` | string | no | New message/comment text. Omit to keep current. |
| `x` | integer | no | New X position. Omit to keep current. |
| `y` | integer | no | New Y position. Omit to keep current. |
| `width` | integer | no | New width. Omit to keep current. |
| `height` | integer | no | New height. Omit to keep current. |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "update_annotation",
  "arguments": {
    "file": {
      "filePath": "contract_annotated.pdf"
    },
    "id": 3,
    "message": "Deadline moved to 15 March \u2014 please confirm"
  }
}
```

## Result

A message of the form `Updated annotation <id> in <file>` naming the saved document.

Pass only what changes: sending just `message` keeps the box where it was; sending `x`/`y` moves the annotation without touching its text.

On failure the text starts with `Annotation update failed for`, followed by the exception type and message.

## Example prompts

* *"Reword comment 3 to mention the new deadline."*
* *"Move the annotation on page 2 down a little — it covers the table header."*
* *"Make annotation 5 bigger so it covers the whole clause."*
