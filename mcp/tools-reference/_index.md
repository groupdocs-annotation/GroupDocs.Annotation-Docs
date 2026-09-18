---
id: mcp-tools-reference
url: annotation/mcp/tools-reference
title: Tools reference
weight: 2
description: "Complete reference of every tool the GroupDocs.Annotation MCP server exposes to AI agents, with parameters, example prompts, and results."
keywords: MCP tools list document annotation, add_annotation MCP tool parameters, get_annotations MCP, annotation replies MCP, MCP tools reference
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

Complete reference of every tool the GroupDocs.Annotation MCP server exposes to AI agents, with parameters, example prompts, and results. Captured from a live `tools/list` call against server version **26.9.0** (raw capture: `tools-list.generated.json` in this section's source).

| Tool | What it does |
|---|---|
| [`get_annotations`]({{< ref "annotation/mcp/tools-reference/get-annotations.md" >}}) | Lists every annotation in a document as JSON, with IDs, positions, and replies |
| [`add_annotation`]({{< ref "annotation/mcp/tools-reference/add-annotation.md" >}}) | Adds a highlight, comment, arrow, or other annotation and saves an annotated copy |
| [`update_annotation`]({{< ref "annotation/mcp/tools-reference/update-annotation.md" >}}) | Edits an existing annotation's message or bounding box |
| [`remove_annotations`]({{< ref "annotation/mcp/tools-reference/remove-annotations.md" >}}) | Removes annotations by ID, or clears all of them |
| [`add_reply`]({{< ref "annotation/mcp/tools-reference/add-reply.md" >}}) | Adds a reply to an existing annotation — comment threads for review cycles |
| [`remove_replies`]({{< ref "annotation/mcp/tools-reference/remove-replies.md" >}}) | Removes replies by ID, by author, or all of them |
| [`export_annotations`]({{< ref "annotation/mcp/tools-reference/export-annotations.md" >}}) | Exports a document's annotations to an XML file |
| [`import_annotations`]({{< ref "annotation/mcp/tools-reference/import-annotations.md" >}}) | Merges annotations from an XML file or another annotated document |
| [`generate_pages_preview`]({{< ref "annotation/mcp/tools-reference/generate-pages-preview.md" >}}) | Renders pages as PNG images the AI client can display inline |
| [`get_document_info`]({{< ref "annotation/mcp/tools-reference/get-document-info.md" >}}) | Returns file type, page count, size, and per-page dimensions |
| [`get_license_status`]({{< ref "annotation/mcp/tools-reference/get-license-status.md" >}}) | Reports the active licensing mode and, under metered licensing, consumption |

## The FileInput shape

Every tool takes its document through the same `file` object — pass **either** a name from your storage folder **or** inline content:

```json
{ "file": { "filePath": "contract.pdf" } }
```

| Field | Type | Description |
|---|---|---|
| `filePath` | string | File path or name in the configured storage folder |
| `fileContent` | string | Base64-encoded file content (alternative to `filePath`) |
| `fileName` | string | Original filename with extension — required with `fileContent`. Since **26.9.0** it also works on its own, resolved from the storage folder exactly like `filePath` |

You rarely write this JSON yourself: the AI agent does, from your plain-language prompt. Missing files are not an error to fear — the tool responds with the list of available files so the agent can correct itself.
