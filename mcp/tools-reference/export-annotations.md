---
id: mcp-tool-export-annotations
url: annotation/mcp/tools-reference/export-annotations
title: export_annotations
weight: 7
description: "The export_annotations MCP tool extracts a document's annotations into an XML file that can be re-imported later or into another copy."
keywords: export_annotations MCP tool, export PDF annotations XML, save annotations separately, migrate annotations between documents
productName: GroupDocs.Annotation MCP Server
generated: true
serverVersion: 26.9.0
toc: True
---

`export_annotations` writes a document's annotations out as an **XML file**, separate from the document itself. That file can be archived, diffed, or fed back in with [`import_annotations`]({{< ref "annotation/mcp/tools-reference/import-annotations.md" >}}). Example prompt: *"Export the review comments so I can keep them with the case file"*.

**Tool description (as the AI agent sees it):**

> Extracts annotations from a document and saves them as an XML file (suitable for re-import via import_annotations). Supports PDF, DOCX, XLSX, PPTX, and 50+ more document and image formats. Call this tool whenever the user asks to export, extract, serialize, or save annotations to XML. Do NOT pre-check whether files exist — pass the filename the user provided directly. Returns a saved-path message ('Exported N annotation(s) from <file> to <name>.annotations.xml'). On failure, the response text starts with 'Annotation export failed for' followed by the underlying exception type, message, and inner-exception chain.

## Parameters

| Name | Type | Required | Description |
|---|---|---|---|
| `file` | object | yes |  — [FileInput shape]({{< ref "annotation/mcp/tools-reference/_index.md#the-fileinput-shape" >}}) |
| `password` | string | no | Password for protected documents |

## Example call

```json
{
  "name": "export_annotations",
  "arguments": {
    "file": {
      "filePath": "contract_annotated.pdf"
    }
  }
}
```

## Result

A saved-path message naming the XML file written to your output folder.

The pair export/import is how annotations move between copies of a document: export from the reviewed copy, import into the revised one, and a round of comments survives a new document version.

On failure the text starts with `Annotation export failed for`, followed by the exception type and message.

## Example prompts

* *"Export the review comments to XML for the case file."*
* *"Save the annotations separately so I can re-apply them to the new draft."*
