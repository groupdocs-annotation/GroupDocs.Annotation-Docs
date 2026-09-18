---
id: mcp-tool-remove-replies
url: annotation/mcp/tools-reference/remove-replies
title: remove_replies
weight: 6
description: "The remove_replies MCP tool removes replies from annotations — by reply ID, by author, or all of them."
keywords: remove_replies MCP tool, delete annotation replies, remove comments by user MCP, clean up document threads
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`remove_replies` removes replies in one of three modes: specific `replyIds`, everything by one `userName`, or — with neither set — **all replies in the document**. Example prompt: *"Remove my replies before I send this on"*.

**Tool description (as the AI agent sees it):**

> Removes replies from annotations and saves the result back to storage. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Filter mode: pass 'replyIds' (comma-separated) to remove by reply ID, OR pass 'userName' to remove all replies from one user. Pass neither to remove ALL replies in the document. Call this tool whenever the user asks to delete a reply, remove a comment thread, or clear replies from one author. Do NOT pre-check whether files exist — pass the filename the user provided directly. Returns a saved-path message ('Removed N reply / replies from <file>'). On failure, the response text starts with 'Reply removal failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `replyIds` | string | no | Comma-separated reply IDs to remove, e.g. '12,34'. Omit to fall back to userName / remove-all. |
| `userName` | string | no | Remove all replies authored by this user name. Mutually exclusive with replyIds. |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "remove_replies",
  "arguments": {
    "file": {
      "filePath": "contract_annotated.pdf"
    },
    "userName": "Alex"
  }
}
```

## Result

A message of the form `Removed N reply / replies from <file>`, naming the saved document.

The three modes are mutually exclusive in practice: pass `replyIds` **or** `userName` **or** neither. Passing neither is the destructive one — it clears every thread in the document.

On failure the text starts with `Reply removal failed for`, followed by the exception type and message.

## Example prompts

* *"Remove my replies before I send this on."*
* *"Delete replies 12 and 34."*
* *"Clear all reply threads but keep the annotations themselves."*
