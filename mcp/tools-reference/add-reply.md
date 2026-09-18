---
id: mcp-tool-add-reply
url: annotation/mcp/tools-reference/add-reply
title: add_reply
weight: 5
description: "The add_reply MCP tool adds a reply to an existing annotation, turning review notes into comment threads."
keywords: add_reply MCP tool, reply to annotation AI agent, document comment thread MCP, review workflow annotations
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`add_reply` adds a reply to an existing annotation, which is what turns isolated notes into **threads**. Call [`get_annotations`]({{< ref "annotation/mcp/tools-reference/get-annotations.md" >}}) first for the target `annotationId`. Example prompt: *"Reply to Maria's comment that finance approved it"*.

**Tool description (as the AI agent sees it):**

> Adds a reply to an existing annotation and saves the result back to storage. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Call get_annotations first to retrieve the target annotation 'id'. Call this tool whenever the user asks to reply to an annotation, add a comment thread, or respond to a review note. Do NOT pre-check whether files exist — pass the filename the user provided directly. Returns a saved-path message ('Added reply to annotation <id> in <file>'). On failure, the response text starts with 'Reply add failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `annotationId` | integer | yes | Annotation ID to reply to (from get_annotations) |
| `comment` | string | yes | Reply comment text |
| `userName` | string | no | Name of the user posting the reply. Defaults to 'mcp-user'. |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "add_reply",
  "arguments": {
    "file": {
      "filePath": "contract_annotated.pdf"
    },
    "annotationId": 3,
    "comment": "Finance approved these terms on 12 March",
    "userName": "Alex"
  }
}
```

## Result

A message naming the saved document with the reply attached to the annotation.

`userName` sets the reply's author; supply it so a later `remove_replies` by author, or a report grouped by reviewer, has something to work with.

On failure the text starts with `Reply failed for`, followed by the exception type and message.

## Example prompts

* *"Reply to Maria's comment that finance approved these terms."*
* *"Answer every open question on page 2 with a short status."*
* *"Add a reply to annotation 4 saying this was fixed in revision 3."*

See it used end-to-end: [Run a review cycle with replies]({{< ref "annotation/mcp/use-cases/review-workflow-with-replies.md" >}}).
