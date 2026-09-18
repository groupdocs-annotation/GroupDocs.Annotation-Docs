---
id: mcp-uc-extract-and-report-annotations
url: annotation/mcp/use-cases/extract-and-report-annotations
title: How to extract and report on document annotations with AI
linkTitle: Report on annotations
weight: 3
description: "Extract annotations from a document with an AI agent over MCP and turn them into a summary, a report grouped by reviewer, or an XML archive."
keywords: extract annotations from PDF, report on document comments AI, export annotations XML, summarize review comments MCP
productName: GroupDocs.Annotation MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "How to extract and report on document annotations with AI"
        description: "Extract annotations from a document with an AI agent over MCP and turn them into a summary, a report grouped by reviewer, or an XML archive."
        steps:
        - name: "Install the server"
          text: "Run the GroupDocs.Annotation MCP server with Docker or dnx and register it in your AI client."
        - name: "Put the documents in the storage folder"
          text: "Point GROUPDOCS_MCP_STORAGE_PATH at the folder that holds the files the agent should use."
        - name: "Ask the agent"
          text: "Summarize the review of contract_annotated.pdf: how many comments, from whom, and what the main themes are."
---

A marked-up document is data, not just ink. [`get_annotations`]({{< ref "annotation/mcp/tools-reference/get-annotations.md" >}}) returns it as JSON — every annotation with its id, type, message, page, author, and replies — and everything an agent can do with a list, it can do with this one.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "annotation/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## Summaries

> Summarize the review of contract_annotated.pdf: how many comments, from whom, and what the main themes are.

One call, then reasoning. No document parsing, no OCR, no guessing.

## Reports that are actually useful

Because the data is structured, the shape of the report is up to your prompt:

> Give me a table: page, author, comment, answered yes/no.
> Group the comments by reviewer and tell me who has the most open items.
> List only the strikeouts — I want to see what people want removed.
> Which pages have no comments at all?

The last one is a question no PDF reader answers easily and the array answers trivially.

## Archiving the comments separately

> Export the annotations so we can keep them with the case file.

[`export_annotations`]({{< ref "annotation/mcp/tools-reference/export-annotations.md" >}}) writes an XML file containing the annotations alone. That file is small, diff-able, and re-importable — useful when the document itself is under retention rules that the commentary is not, or when you want to compare two review rounds.

## Comparing rounds

Two exports of the same document, before and after a review round, are two text files. Ask the agent to compare them and you get *"three new comments, two resolved, one reworded"* — a changelog of the review rather than of the document.

## Feeding a wider workflow

The change list is ordinary JSON, so the agent can carry it onward: open an issue per unanswered comment, draft the reply email, or produce the summary paragraph for a status report. What it should **not** do is treat annotation text as trusted instructions — comments come from other people, and an agent that acts on *"ignore previous instructions"* inside a comment is a problem. Ask for summaries and reports; keep actions under your own review.

## The evaluation trap

A trial badge on every page does not change the annotation data, so reports built this way are accurate even unlicensed. The badge only affects what you can *send*. If the plan ends in "and email them the marked-up copy", check [`get_license_status`]({{< ref "annotation/mcp/tools-reference/get-license-status.md" >}}) first.
