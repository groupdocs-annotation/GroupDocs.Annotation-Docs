---
id: mcp-troubleshooting-faq
url: annotation/mcp/troubleshooting-faq
title: Troubleshooting & FAQ
weight: 5
description: "Solutions to the most common GroupDocs.Annotation MCP server issues — server not appearing in the client, startup failures, missing native dependencies, and first-launch timeouts."
keywords: MCP server not showing up in Claude Desktop, Claude can't see MCP tools, MCP server failed to start, dnx command not found, libgdiplus not found error, annotate documents AI agent, add comments to PDF with AI, document review MCP, extract annotations MCP
productName: GroupDocs.Annotation MCP Server
toc: True
---

Solutions to the most common GroupDocs.Annotation MCP server issues — server not appearing in the client, startup failures, missing native dependencies, and first-launch timeouts.

{{< alert style="info" >}}
**Platform-specific troubleshooting:** runtime problems depend on which build you run. For the `dnx` runner, native graphics libraries, and the Docker channel, see [Troubleshooting (.NET)]({{< ref "annotation/net/mcp/troubleshooting.md" >}}). The issues on this page apply to every platform.
{{< /alert >}}

## Why is my MCP server not showing up in Claude Desktop?

1. **Restart the client** — every client reads its MCP config only at startup.
2. Check the config file location for your OS ([per-client reference]({{< ref "annotation/net/mcp/install-in-ai-clients.md" >}})) and that the entry sits under the right root key (`mcpServers` for Claude Desktop/Cursor/Windsurf, `servers` for VS Code/VS 2022).
3. Validate the JSON — a trailing comma silently breaks the whole file. If you used the [installer](https://github.com/groupdocs/GroupDocs.Mcp.Installer), a timestamped `.bak` of your previous config sits next to the file for comparison.

## The first tool call is slow or fails once, then works

A **cold cache**: on the very first use the server's package or image is still downloading while the client is already waiting on the connection. Warming it once fixes it for good — the exact command depends on your build: [.NET]({{< ref "annotation/net/mcp/troubleshooting.md" >}}#the-first-tool-call-is-slow-or-fails-once-and-then-works).

## The server fails to start, or a runtime dependency is missing

These are properties of the build you run rather than of MCP, so the fixes live with the platform:

| Symptom | Where the fix is |
|---|---|
| `dnx: command not found` | [.NET troubleshooting]({{< ref "annotation/net/mcp/troubleshooting.md" >}}#dnx-command-not-found) — `dnx` ships inside the .NET 10 SDK |
| `DllNotFoundException: libgdiplus` on Linux/macOS | [.NET troubleshooting]({{< ref "annotation/net/mcp/troubleshooting.md" >}}#dllnotfoundexception-libgdiplus) — install the native graphics libraries, or use the Docker image |
| "docker daemon not reachable" | [.NET troubleshooting]({{< ref "annotation/net/mcp/troubleshooting.md" >}}#docker-daemon-not-reachable) — start Docker Desktop or `dockerd` |

## The agent says a file does not exist

Pass the **file name**, not a full path from your machine: the server resolves names inside its configured storage folder. When a name is not found the tool responds with the list of files it can see, so the agent can correct itself — check that list against [`GROUPDOCS_MCP_STORAGE_PATH`]({{< ref "annotation/net/mcp/configuration.md" >}}).

## The annotation IDs keep changing — which one do I pass?

Always call [`get_annotations`]({{< ref "annotation/mcp/tools-reference/get-annotations.md" >}}) first and use the `id` from that response. IDs identify annotations inside the document you just read; after a tool writes a new file, re-read the **new** file before updating or removing anything in it.

## Which file does the agent write to?

`add_annotation` saves a new document named `<name>_annotated.<ext>` — your original is never modified. The reply and removal tools save the result back to storage too, so a review cycle produces a chain of files rather than mutating one in place. Keep an eye on which file name the agent passes to the next call.

## What annotation types are supported?

`textfield`, `area`, `point`, `arrow`, `highlight`, `underline`, and `strikeout`. The underlying library supports more; these are the ones exposed as MCP tool parameters today. If you need another type through MCP, say so in the [forum](https://forum.groupdocs.com/c/annotation/10).

## Can the agent see the document?

Yes — [`generate_pages_preview`]({{< ref "annotation/mcp/tools-reference/generate-pages-preview.md" >}}) renders pages as PNG images and returns them inline, with annotations baked in. In a client that supports image content (Claude Desktop, for example) the agent can look at the page it just annotated and describe or check its own work.

## Do coordinates need to be exact?

`x`/`y` are document coordinates, and an agent guessing them from a prompt will place an `area` or `point` annotation approximately. For precise placement, render a preview first, or annotate an existing element by reading its bounding box from `get_annotations`.

## Verifying an installation end-to-end

Ask your agent *"list your GroupDocs annotation tools and the license status"* — it should name `get_annotations`, `add_annotation`, `update_annotation`, `remove_annotations`, `add_reply`, `remove_replies`, `export_annotations`, `import_annotations`, `generate_pages_preview`, `get_document_info`, `get_license_status`. For a scripted check that performs the real MCP handshake and a live call through the engine, see [verifying a .NET installation]({{< ref "annotation/net/mcp/troubleshooting.md" >}}#verifying-an-installation-end-to-end).

## Still stuck?

Post your config (redact license paths) and the client name in the [Annotation forum](https://forum.groupdocs.com/c/annotation/10) — we answer MCP questions daily. Bugs: [GitHub issues](https://github.com/groupdocs-annotation/GroupDocs.Annotation.Mcp/issues).
