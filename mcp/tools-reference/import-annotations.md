---
id: mcp-tool-import-annotations
url: annotation/mcp/tools-reference/import-annotations
title: import_annotations
weight: 8
description: "The import_annotations MCP tool merges annotations from an XML file or another annotated document into a target document."
keywords: import_annotations MCP tool, merge annotations documents, apply annotations to new version, combine reviewer comments MCP
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`import_annotations` merges annotations into a document from a **source** — either an XML file produced by `export_annotations`, or another annotated document. This is how a round of comments survives a new draft, and how several reviewers' copies are combined. Example prompt: *"Apply the comments from the old draft to the new one"*.

**Tool description (as the AI agent sees it):**

> Imports annotations from another source (an XML annotations file or an annotated document) and saves the merged document back to storage. Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats for the target. Source must be either an XML file produced by export_annotations, or another annotated document of the same engine format. Call this tool whenever the user asks to import, merge, or apply annotations from one document to another. Do NOT pre-check whether files exist — pass the filenames the user provided directly. Returns a saved-path message ('Imported annotations from <source> into <file>'). On failure, the response text starts with 'Annotation import failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `source` | object | yes | Source file containing annotations to import — an XML file (.xml) or an annotated document (.pdf, .docx, etc.). — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `password` | string | no | Password for protected target documents |

## Example call

```json
{
  "name": "import_annotations",
  "arguments": {
    "file": {
      "filePath": "contract-v2.pdf"
    },
    "source": {
      "filePath": "contract-v1-annotations.xml"
    }
  }
}
```

## Result

A message of the form `Imported annotations from <source> into <file>`, naming the merged document.

The source document must be the same engine format as the target — annotations from a PDF go into a PDF. Coordinates come across as-is, so on a re-flowed draft an imported note may land near, rather than exactly on, the text it referred to.

On failure the text starts with `Annotation import failed for`, followed by the exception type and message.

## Example prompts

* *"Apply the comments from the old draft to the new version."*
* *"Merge the annotations from both reviewers into one copy."*
* *"Import the annotations XML into this document."*
