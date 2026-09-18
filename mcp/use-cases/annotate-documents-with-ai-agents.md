---
id: mcp-uc-annotate-documents-with-ai-agents
url: annotation/mcp/use-cases/annotate-documents-with-ai-agents
title: How to annotate documents with AI agents using MCP
linkTitle: Annotate with AI agents
weight: 1
description: "Annotate documents with an AI agent over MCP: the agent reads your instruction, the GroupDocs engine writes the annotation locally, and an annotated copy appears in your output folder."
keywords: annotate documents with AI agent, MCP document annotation, Claude annotate PDF, AI highlight document
productName: GroupDocs.Annotation MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "How to annotate documents with AI agents using MCP"
        description: "Annotate documents with an AI agent over MCP: the agent reads your instruction, the GroupDocs engine writes the annotation locally, and an annotated copy appears in your output folder."
        steps:
        - name: "Install the server"
          text: "Run the GroupDocs.Annotation MCP server with Docker or dnx and register it in your AI client."
        - name: "Put the documents in the storage folder"
          text: "Point GROUPDOCS_MCP_STORAGE_PATH at the folder that holds the files the agent should use."
        - name: "Ask the agent"
          text: "Highlight the payment clause, then on the resulting file strike out the old delivery date, then show me page 2."
---

Annotating with an AI agent works because the two halves do what each is good at: the **agent** understands *"flag anything that shifts risk to us"*, and the **engine** writes a real annotation into a real document, locally.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "annotation/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## The pattern

1. Put the document in the storage folder the server can see.
2. Ask in plain language: *"Highlight the payment clause on page 2 and add a note asking legal to confirm."*
3. The agent calls [`add_annotation`]({{< ref "annotation/mcp/tools-reference/add-annotation.md" >}}) with the type, text, page, and position.
4. The engine writes `contract_annotated.pdf` next to your original — **the original is never modified**.
5. Optionally the agent calls [`generate_pages_preview`]({{< ref "annotation/mcp/tools-reference/generate-pages-preview.md" >}}) and looks at the result.

## The one thing that trips people up

Every writing tool saves a **new file** named `<name>_annotated.<ext>`. So a second annotation must be applied to *that* file, not to the original — otherwise the first annotation is silently left behind in a file nobody opens again.

A well-instructed agent chains them:

> Highlight the payment clause, then on the resulting file strike out the old delivery date, then show me page 2.

If you are scripting the calls yourself, pass the file name returned by the previous call. If an annotation "disappears", this is almost always why.

## Placement, honestly

`x`/`y` are document coordinates. An agent asked to *"highlight the payment clause"* has to guess where that clause is unless something tells it. Three ways to get placement right:

* **Read first** — [`get_annotations`]({{< ref "annotation/mcp/tools-reference/get-annotations.md" >}}) returns bounding boxes of existing annotations to anchor against.
* **Look first** — render the page with `generate_pages_preview` and let a vision-capable model locate the text.
* **Check after** — annotate, render, and let the agent adjust with [`update_annotation`]({{< ref "annotation/mcp/tools-reference/update-annotation.md" >}}) if the box landed badly.

Use `get_document_info` for the page box before placing anything near an edge.

## Setup

```bash
dnx GroupDocs.Annotation.Mcp --yes
```

with `GROUPDOCS_MCP_STORAGE_PATH` pointing at your documents folder — [exact per-client config]({{< ref "annotation/net/mcp/install-in-ai-clients.md" >}}), or run the [installer]({{< ref "annotation/mcp/getting-started/_index.md" >}}).

## Where to go next

* [Run a review cycle with replies]({{< ref "annotation/mcp/use-cases/review-workflow-with-replies.md" >}}) — threads, authors, and resolving comments.
* [Extract and report on annotations]({{< ref "annotation/mcp/use-cases/extract-and-report-annotations.md" >}}) — turn a marked-up document into a summary.
* [Let the agent see the page]({{< ref "annotation/mcp/use-cases/visual-preview-for-agents.md" >}}) — inline rendering, and why it matters.
* [On-premise architecture]({{< ref "annotation/mcp/use-cases/on-premise-document-annotation.md" >}}) — what stays local.
