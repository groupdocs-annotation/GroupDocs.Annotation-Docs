---
id: mcp-uc-review-workflow-with-replies
url: annotation/mcp/use-cases/review-workflow-with-replies
title: How to run a document review cycle with an AI agent
linkTitle: Review cycle with replies
weight: 2
description: "Run a document review cycle with an AI agent over MCP: list open comments, reply in threads with author names, resolve what is done, and hand back a clean copy."
keywords: document review workflow AI, reply to annotations agent, comment threads document MCP, resolve review comments AI
productName: GroupDocs.Annotation MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "How to run a document review cycle with an AI agent"
        description: "Run a document review cycle with an AI agent over MCP: list open comments, reply in threads with author names, resolve what is done, and hand back a clean copy."
        steps:
        - name: "Install the server"
          text: "Run the GroupDocs.Annotation MCP server with Docker or dnx and register it in your AI client."
        - name: "Put the documents in the storage folder"
          text: "Point GROUPDOCS_MCP_STORAGE_PATH at the folder that holds the files the agent should use."
        - name: "Ask the agent"
          text: "List the annotations in contract_annotated.pdf. Which ones have no replies?"
---

A review round is rarely *"add a comment"*. It is: what is still open, who raised it, answer it, resolve it, and produce a clean copy for the next audience. All five are tool calls.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "annotation/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## 1. What is open?

> List the annotations in contract_annotated.pdf. Which ones have no replies?

[`get_annotations`]({{< ref "annotation/mcp/tools-reference/get-annotations.md" >}}) returns every annotation with its `id`, author, page, message, and `replies`. "Unanswered" is just an empty replies array — the agent filters the list it already has, without re-reading the document.

## 2. Answer in threads

> Reply to Maria's comment that finance approved the terms on 12 March. Sign it as Alex.

[`add_reply`]({{< ref "annotation/mcp/tools-reference/add-reply.md" >}}) takes the `annotationId` from step 1, the `comment`, and a `userName`. Supply the name: a thread without authors cannot be filtered later, and [`remove_replies`]({{< ref "annotation/mcp/tools-reference/remove-replies.md" >}}) can clean up by author only if the author was recorded.

## 3. Resolve what is done

There is no "resolved" flag in the model — resolution is a convention you choose:

* **Reply and leave it** — the thread is the audit trail; nothing is deleted.
* **Remove the annotation** — [`remove_annotations`]({{< ref "annotation/mcp/tools-reference/remove-annotations.md" >}}) by id once an issue is closed, keeping only open points.
* **Edit the message** — [`update_annotation`]({{< ref "annotation/mcp/tools-reference/update-annotation.md" >}}) to prefix `[RESOLVED]`, which keeps the history visible in any viewer.

Pick one and tell the agent which: *"mark resolved by prefixing the message, do not delete anything"* is a perfectly good instruction.

## 4. Carry the round to the next draft

The document changes; the comments should not be lost:

> Export the annotations from the reviewed copy, then import them into contract-v3.pdf.

[`export_annotations`]({{< ref "annotation/mcp/tools-reference/export-annotations.md" >}}) writes an XML file; [`import_annotations`]({{< ref "annotation/mcp/tools-reference/import-annotations.md" >}}) merges it into the new draft. Coordinates carry over as-is, so on a re-flowed document a note may land near rather than exactly on its original text — worth a preview pass afterwards.

The same pair merges two reviewers' copies into one.

## 5. Hand back something clean

> Remove all annotations and give me a clean copy for the counterparty.

`remove_annotations` with no `ids` clears everything into a new file. Ask the agent to confirm the count before it runs — this is the one call in the workflow with no undo.

## Keeping the trail honest

Two habits make this workflow trustworthy:

* **Always name the file you mean.** Each step writes a new file; the agent should pass the previous result forward, not the original.
* **Check the licence before a formal review.** In evaluation mode every page carries a trial badge, which is not something to send to a counterparty — [`get_license_status`]({{< ref "annotation/mcp/tools-reference/get-license-status.md" >}}) answers in one call.
