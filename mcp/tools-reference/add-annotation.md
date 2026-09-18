---
id: mcp-tool-add-annotation
url: annotation/mcp/tools-reference/add-annotation
title: add_annotation
weight: 2
description: "The add_annotation MCP tool adds a highlight, comment, arrow, area, point, underline, or strikeout to a document and saves an annotated copy."
keywords: add_annotation MCP tool, highlight PDF with AI agent, add comment to document MCP, annotate document AI
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`add_annotation` adds an annotation — `textfield`, `area`, `point`, `arrow`, `highlight`, `underline`, or `strikeout` — and saves the result as `<name>_annotated.<ext>`. Your original file is never modified. Example prompt: *"Highlight the payment clause and add a note for legal"*.

**Tool description (as the AI agent sees it):**

> Adds an annotation to a document and saves the annotated file as '<name>_annotated.<ext>'. Supported types: textfield, area, point, arrow, highlight, underline, strikeout. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Call this tool whenever the user asks to annotate, comment, highlight, underline, strikeout, or mark up a document. Do NOT pre-check whether files exist — pass the filename the user provided directly. The tool resolves files from storage and returns an error with available files if a name is not found. Returns a saved-path message ('Added <type> annotation to <file> on page <n>') with the download URL or storage path. On failure, the response text starts with 'Annotation failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `type` | string | yes | Annotation type: textfield, area, point, arrow, highlight, underline, strikeout |
| `text` | string | yes | Annotation text or comment |
| `page` | integer | no | Page number (1-based) |
| `x` | integer | no | X position (document coordinates) |
| `y` | integer | no | Y position (document coordinates) |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "add_annotation",
  "arguments": {
    "file": {
      "filePath": "contract.pdf"
    },
    "type": "highlight",
    "text": "Confirm these payment terms with legal",
    "page": 2,
    "x": 100,
    "y": 250
  }
}
```

## Result

A message naming the saved file — `Added <type> annotation to <file> on page <n>` — with the storage path of the annotated copy.

Because the tool writes `<name>_annotated.<ext>` rather than editing in place, a sequence of annotations should be applied to the **result** of the previous call, not to the original; otherwise each call starts from the unannotated document again.

On failure the text starts with `Annotation failed for`, followed by the exception type and message.

## Example prompts

* *"Highlight the payment clause on page 2 and add a note asking legal to confirm."*
* *"Strike out the deprecated paragraph and explain why in the comment."*
* *"Add a point annotation on page 1 saying the logo is outdated."*
* *"Underline every date on page 4 and flag them for review."*

See it used end-to-end: [Annotate documents with AI agents]({{< ref "annotation/mcp/use-cases/annotate-documents-with-ai-agents.md" >}}).
