---
id: mcp-uc-visual-preview-for-agents
url: annotation/mcp/use-cases/visual-preview-for-agents
title: How to let an AI agent see the document page it annotated
linkTitle: Page previews for agents
weight: 4
description: "Render document pages as inline PNG images over MCP so an AI agent can look at the page it just annotated, verify placement, and correct it."
keywords: render document page for AI agent, inline image MCP tool, agent sees document, verify annotation placement AI
productName: GroupDocs.Annotation MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "How to let an AI agent see the document page it annotated"
        description: "Render document pages as inline PNG images over MCP so an AI agent can look at the page it just annotated, verify placement, and correct it."
        steps:
        - name: "Install the server"
          text: "Run the GroupDocs.Annotation MCP server with Docker or dnx and register it in your AI client."
        - name: "Put the documents in the storage folder"
          text: "Point GROUPDOCS_MCP_STORAGE_PATH at the folder that holds the files the agent should use."
        - name: "Ask the agent"
          text: "Highlight the payment clause on page 2, then show me the page."
---

Most document tools are write-only: the agent calls them and reports success because the call returned. [`generate_pages_preview`]({{< ref "annotation/mcp/tools-reference/generate-pages-preview.md" >}}) breaks that pattern — it renders pages as **PNG images returned inline**, with annotations baked in, so a vision-capable model can actually look.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "annotation/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## The loop

> Highlight the payment clause on page 2, then show me the page.

1. [`add_annotation`]({{< ref "annotation/mcp/tools-reference/add-annotation.md" >}}) writes `contract_annotated.pdf`.
2. `generate_pages_preview` on that file with `pages: "2"` returns the rendered page as an image block.
3. The agent sees where the highlight landed — and if it landed on the wrong paragraph, [`update_annotation`]({{< ref "annotation/mcp/tools-reference/update-annotation.md" >}}) moves it without starting over.

That third step is the difference between *"I added a highlight"* and *"the highlight is on the payment clause"*.

## What you need for it to work

* **A client that renders image content.** Claude Desktop does; a terminal client may only report that an image was returned. The tool behaves the same either way — the images simply may not be displayed.
* **A model that can see.** The images are only useful to a vision-capable model.
* **Patience for big pages.** Rendering is the most expensive call this server makes. Ask for `pages: "2"` or `"1-3"`, not a fifty-page document.

## Other things the preview is good for

* **Locating text before annotating** — render first, let the model read the page, then place the annotation with coordinates it derived rather than guessed.
* **Showing a reviewer the result** in chat, without opening the file.
* **Checking a merge** — after [`import_annotations`]({{< ref "annotation/mcp/tools-reference/import-annotations.md" >}}) onto a re-flowed draft, a preview shows whether imported notes still sit where they mean to.
* **Sanity-checking the licence state** — a trial badge is visible in the rendered page, which is a blunt but effective check.

## Prompts that work

> Render pages 1-3 of the annotated contract so I can check the comments.
> Show me page 2, then tell me whether the highlight covers the whole clause.
> Preview the first page and describe what is on it.

## A note on cost and privacy

The rendering happens locally — the PNG is produced by the engine on your machine. But the image then travels to your model provider like any other message content: with a cloud-hosted model, previewing a page means sending a picture of that page. For sensitive documents, that is the moment to use a local model. See [On-premise architecture]({{< ref "annotation/mcp/use-cases/on-premise-document-annotation.md" >}}).
