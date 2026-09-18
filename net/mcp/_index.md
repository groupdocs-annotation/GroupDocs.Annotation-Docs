---
id: mcp-net
url: annotation/net/mcp
title: MCP server for .NET
linkTitle: MCP Server
weight: 7
description: "Install and configure the GroupDocs.Annotation MCP server for .NET — one-click install links for VS Code and Cursor, per-OS setup for Windows, Linux, and macOS, and the full environment-variable reference."
keywords: GroupDocs.Annotation MCP .NET, install MCP server dnx, MCP server Docker image, MCP server configuration, Model Context Protocol .NET
productName: GroupDocs.Annotation MCP Server for .NET
hideChildren: True
toc: True
---

Everything needed to **install and run** the GroupDocs.Annotation MCP server on the .NET platform. What the server *does* — its tools, use cases, and licensing model — is platform-independent and lives in the [MCP server section]({{< ref "annotation/mcp/_index.md" >}}).

| The .NET build at a glance | |
|---|---|
| Package | [`GroupDocs.Annotation.Mcp`](https://www.nuget.org/packages/GroupDocs.Annotation.Mcp) (current **26.9.0**) |
| One-command run | `dnx GroupDocs.Annotation.Mcp --yes` |
| Container images | `ghcr.io/groupdocs-annotation/annotation-net-mcp` · `groupdocs/annotation-net-mcp` |
| Prerequisites | [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0) for the NuGet channel, or Docker |
| Source | [GroupDocs.Annotation.Mcp on GitHub](https://github.com/groupdocs-annotation/GroupDocs.Annotation.Mcp) |
| Release notes | [changelog](https://github.com/groupdocs-annotation/GroupDocs.Annotation.Mcp/tree/master/changelog) · [GitHub releases](https://github.com/groupdocs-annotation/GroupDocs.Annotation.Mcp/releases) |

## Start here

1. **Install** for your operating system — [Windows]({{< ref "annotation/net/mcp/windows-installation.md" >}}) · [Linux]({{< ref "annotation/net/mcp/linux-installation.md" >}}) · [macOS]({{< ref "annotation/net/mcp/macos-installation.md" >}})
2. **Register it in your AI client** — [one-click links and per-client configs]({{< ref "annotation/net/mcp/install-in-ai-clients.md" >}})
3. **Point it at your documents** — [configuration]({{< ref "annotation/net/mcp/configuration.md" >}})
4. **License it** — evaluation, a license file, or metered keys: [Licensing]({{< ref "annotation/mcp/getting-started/licensing.md" >}})

## In this section

* [Install on Windows]({{< ref "annotation/net/mcp/windows-installation.md" >}})
* [Install on Linux]({{< ref "annotation/net/mcp/linux-installation.md" >}})
* [Install on macOS]({{< ref "annotation/net/mcp/macos-installation.md" >}})
* [Register in AI clients]({{< ref "annotation/net/mcp/install-in-ai-clients.md" >}}) — VS Code, Cursor, Claude, Visual Studio, Windsurf, Cline, Codex, Rider
* [Configuration]({{< ref "annotation/net/mcp/configuration.md" >}}) — storage, output, license, metered keys
* [System requirements]({{< ref "annotation/net/mcp/system-requirements.md" >}})
* [Troubleshooting (.NET)]({{< ref "annotation/net/mcp/troubleshooting.md" >}}) — `dnx`, native libraries, Docker daemon

## Platform-independent reference

* [Tools reference]({{< ref "annotation/mcp/tools-reference/_index.md" >}}) — `get_annotations`, `add_annotation`, `update_annotation`, `remove_annotations`, `add_reply`, `remove_replies`, `export_annotations`, `import_annotations`, `generate_pages_preview`, `get_document_info`, `get_license_status`
* [Use cases]({{< ref "annotation/mcp/use-cases/_index.md" >}}) · [Supported formats]({{< ref "annotation/mcp/supported-formats.md" >}}) · [Troubleshooting & FAQ]({{< ref "annotation/mcp/troubleshooting-faq.md" >}})
