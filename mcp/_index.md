---
id: mcp
url: annotation/mcp
title: GroupDocs.Annotation MCP Server
weight: 6
description: "GroupDocs.Annotation MCP server lets AI agents like Claude, Cursor, and Copilot annotate, review, and comment on documents — PDF, Word, Excel, PowerPoint and 50+ formats — locally on your machine."
keywords: document annotation MCP server, annotate PDF with AI agent, document review MCP, add comments to documents AI, Claude annotate files locally
productName: GroupDocs.Annotation MCP Server
hideChildren: True
toc: True
---

**GroupDocs.Annotation MCP server** lets AI agents like Claude, Cursor, and Copilot **annotate and review documents** — PDF, Word, Excel, PowerPoint, images, and 50+ more formats — **locally on your machine**. Highlights, comments, arrows, strikeouts, and full reply threads, with nothing uploaded to any cloud service. 

Run it with one command. The Docker image is self-contained — the runtime and every native dependency the engine needs are inside it:

```bash
docker run --rm -i -v $(pwd)/documents:/data \
  ghcr.io/groupdocs-annotation/annotation-net-mcp:latest
```

With the .NET 10 SDK installed, the same server also runs without Docker:

```bash
dnx GroupDocs.Annotation.Mcp --yes
```

Both are the **.NET** build of the server and run on Windows, Linux, and macOS. Other platforms will each get their own launcher — see [Install for your platform](#install-for-your-platform).

Or use the [guided installer]({{< ref "annotation/mcp/getting-started/_index.md" >}}) to register the server in your AI client, verify the setup, and configure shared folders in one pass.

## What you can do

Eleven tools, which fall into four groups (full details in the [tools reference]({{< ref "annotation/mcp/tools-reference/_index.md" >}})):

**Read** — [`get_annotations`]({{< ref "annotation/mcp/tools-reference/get-annotations.md" >}}) lists every annotation as JSON (ids, types, pages, authors, replies); [`get_document_info`]({{< ref "annotation/mcp/tools-reference/get-document-info.md" >}}) returns pages and dimensions.

**Write** — [`add_annotation`]({{< ref "annotation/mcp/tools-reference/add-annotation.md" >}}) adds a highlight, comment, arrow, area, point, underline, or strikeout; [`update_annotation`]({{< ref "annotation/mcp/tools-reference/update-annotation.md" >}}) edits one; [`remove_annotations`]({{< ref "annotation/mcp/tools-reference/remove-annotations.md" >}}) deletes by id or clears all.

**Discuss** — [`add_reply`]({{< ref "annotation/mcp/tools-reference/add-reply.md" >}}) and [`remove_replies`]({{< ref "annotation/mcp/tools-reference/remove-replies.md" >}}) turn annotations into threads, with authors.

**Move and show** — [`export_annotations`]({{< ref "annotation/mcp/tools-reference/export-annotations.md" >}}) / [`import_annotations`]({{< ref "annotation/mcp/tools-reference/import-annotations.md" >}}) carry a round of comments to a new draft; [`generate_pages_preview`]({{< ref "annotation/mcp/tools-reference/generate-pages-preview.md" >}}) renders pages as images the client displays inline.

Ask in plain language — *"highlight the payment clause and ask legal to confirm"*, *"which comments are still unanswered?"* — and the agent picks the tools.

## Install for your platform

Installation, prerequisites, and client configuration are platform-specific; the tools and licensing model below are the same everywhere.

| Platform | Status | Install and setup |
|---|---|---|
| .NET | **Available** | [MCP server for .NET]({{< ref "annotation/net/mcp/_index.md" >}}) |
| Java | Planned | [Tell us you need it](https://forum.groupdocs.com/c/annotation/10) |
| Python | Planned | [Tell us you need it](https://forum.groupdocs.com/c/annotation/10) |
| Node.js | Planned | [Tell us you need it](https://forum.groupdocs.com/c/annotation/10) |

## The agent can see what it annotated

Most document servers are write-only: the agent calls a tool and trusts the result. `generate_pages_preview` returns **rendered PNGs inline**, annotations included, so in a client with image support the agent can look at the page it just marked up, check the placement, and fix it before you ever open the file. Details: [Let the agent see the page]({{< ref "annotation/mcp/use-cases/visual-preview-for-agents.md" >}}).

## Supported AI clients

| Client | How it connects |
|---|---|
| Claude Desktop | `claude_desktop_config.json` |
| Claude Code | `claude mcp add` CLI |
| VS Code / GitHub Copilot | user-level or workspace `mcp.json` |
| Visual Studio 2022 (17.14+) | `.mcp.json` in the solution root |
| Cursor | `~/.cursor/mcp.json` |
| Windsurf | `~/.codeium/windsurf/mcp_config.json` |
| Cline | Cline MCP settings |
| Codex CLI | `codex mcp add` CLI |
| JetBrains Rider | manual registration (Settings → AI Assistant → MCP) |

Exact config blocks for every client: [Register in AI clients]({{< ref "annotation/net/mcp/install-in-ai-clients.md" >}}).

## Delivery channels

| | Docker (recommended) | NuGet (`dnx`) |
|---|---|---|
| Prerequisites | Docker only | .NET 10 SDK (+ `libgdiplus` on Linux/macOS) |
| Native dependencies | bundled in the image | installed by you (or the setup script) |
| Package | `ghcr.io/groupdocs-annotation/annotation-net-mcp` | `GroupDocs.Annotation.Mcp` on NuGet |
| Architectures | linux/amd64 + linux/arm64 (Apple Silicon native) | any OS with .NET 10 |

## How it works

The server uses MCP's **local stdio transport**: your AI client starts the server as a child process and talks to it over standard input/output. No inbound ports, no external endpoints, no telemetry — the data path is *agent → local server → local filesystem*. Review comments are often more sensitive than the document itself; this keeps both on your machine. Details: [On-premise architecture]({{< ref "annotation/mcp/use-cases/on-premise-document-annotation.md" >}}).

## When you need more than a PDF viewer's comments

A PDF reader can annotate a PDF. Choose this server when you need: the **same annotation model across 50+ formats** (Word, Excel, PowerPoint, images — not just PDF); annotations as **structured data** an agent can filter, count, and report on; **threads with authors** rather than loose notes; export/import so a review survives a new draft; and the fidelity of the commercial GroupDocs engine trusted by enterprise teams for over a decade.

## Resources

* [Quick start]({{< ref "annotation/mcp/getting-started/_index.md" >}}) · [Use cases]({{< ref "annotation/mcp/use-cases/_index.md" >}}) · [Troubleshooting & FAQ]({{< ref "annotation/mcp/troubleshooting-faq.md" >}})
* GitHub: [server source](https://github.com/groupdocs-annotation/GroupDocs.Annotation.Mcp) · [installer](https://github.com/groupdocs/GroupDocs.Mcp.Installer) · [integration tests](https://github.com/groupdocs-annotation/GroupDocs.Annotation.Mcp.Tests)
* [NuGet package](https://www.nuget.org/packages/GroupDocs.Annotation.Mcp) · [Docker image](https://github.com/orgs/groupdocs-annotation/packages/container/package/annotation-net-mcp) · [MCP Registry](https://registry.modelcontextprotocol.io/v0/servers?search=io.github.groupdocs-annotation/groupdocs-annotation-mcp)
* Questions: [Annotation forum](https://forum.groupdocs.com/c/annotation/10)
