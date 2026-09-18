---
id: mcp-uc-on-premise-document-annotation
url: annotation/mcp/use-cases/on-premise-document-annotation
title: "Running GroupDocs MCP servers on-premise: architecture and security model"
linkTitle: On-premise deployment
weight: 5
description: "Run document annotation for AI agents fully on-premise: local stdio transport, no external endpoints, no inbound ports, no telemetry — the architecture and security model in one page."
keywords: on-premise MCP server, air-gapped document annotation, MCP security model, local document processing AI, no cloud document review
productName: GroupDocs.Annotation MCP Server
toc: True
structuredData:
    showOrganization: True
    howTo:
        name: "Running GroupDocs MCP servers on-premise: architecture and security model"
        description: "Run document annotation for AI agents fully on-premise: local stdio transport, no external endpoints, no inbound ports, no telemetry — the architecture and security model in one page."
        steps:
        - name: "Run the pinned image inside the perimeter"
          text: "Start the GroupDocs.Annotation MCP server from its versioned Docker image as a child process of the AI client."
        - name: "Mount only the folders the agent may reach"
          text: "Map the document folder read-write and the license folder read-only."
        - name: "Choose the license mode"
          text: "Use a license file for fully offline operation; metered licensing needs outbound egress for usage reports."
---

Run document annotation for AI agents **fully on-premise**: the GroupDocs.Annotation MCP server uses local stdio transport with **no external endpoints, no inbound ports, and no telemetry** — suitable for regulated environments where documents cannot leave the network. This page is the one to send your security reviewer.

{{< alert style="info" >}}
The commands and config snippets on this page are for the **.NET** build of the server — the only platform available today. Installation and client setup: [MCP server for .NET]({{< ref "annotation/net/mcp/_index.md" >}}). Other platforms will expose the same tools with their own launch command; everything else on this page applies unchanged.
{{< /alert >}}

## The architecture in one picture

```text
+--------------+          +--------------------+         +------------------+
|  AI client   |  stdio   | MCP server process | reads / | local filesystem |
| (Claude, VS  | <----->  | (GroupDocs engine) | <-----> | storage / output |
| Code, agent) | JSON-RPC |   child process    |  writes |     folders      |
+--------------+          +--------------------+         +------------------+
```

* **Transport:** the AI client *starts the server as a child process* and communicates over standard input/output. The server never listens on a network socket — there is nothing to firewall, nothing to expose.
* **Data path:** agent → local server → local filesystem. Documents and annotated copies are read and written in the folders you configure; no document content is transmitted anywhere.
* **Network use:** only at install time (pulling the package from nuget.org or the image from ghcr.io/docker.io). At runtime the server makes no outbound calls. In an air-gapped segment, pre-pull the image or pre-cache the package and pin the version.
* **Telemetry:** none. The server does not phone home, and the engine processes documents in-process.

## Two things specific to annotation

**Comments are content.** The annotation text an agent writes, and the existing comments it reads back, travel through the conversation like any other text. With a cloud-hosted model, *"summarize the review comments"* sends those comments to the model provider. The documents stay local unconditionally; the commentary goes wherever your model runs.

**Previews are pictures of your document.** [`generate_pages_preview`]({{< ref "annotation/mcp/tools-reference/generate-pages-preview.md" >}}) renders locally, but the resulting image is returned to the client and therefore to the model. It is the single highest-exposure call in this server — worth knowing before someone previews a page of a sealed filing.

Pair the server with a locally-hosted model and both concerns disappear: the entire loop stays inside the perimeter.

## Docker deployment inside the perimeter

```bash
docker run --rm -i \
  -v /srv/review:/data \
  -v /srv/licenses:/license:ro \
  -e GROUPDOCS_MCP_STORAGE_PATH=/data \
  -e GROUPDOCS_LICENSE_PATH=/license/GroupDocs.Annotation.lic \
  ghcr.io/groupdocs-annotation/annotation-net-mcp:26.9.0
```

* Pin the tag (`:26.9.0`, not `:latest`) so a rebuild cannot change behaviour underneath you.
* Mount the licence read-only; mount only the folders the agent should reach.
* Images are multi-arch (linux/amd64 + linux/arm64) and carry every native dependency, which also removes the `libgdiplus` class of problem.

## License management

* **License file** — read from local disk by the local process. Fully offline; the right answer for air-gapped deployments.
* **Metered (pay-per-use)** — reports *usage* to GroupDocs servers, so it needs outbound egress. Document content is never part of that report, but the connection must be allowed.

Both are covered in [Licensing]({{< ref "annotation/mcp/getting-started/licensing.md" >}}), including how to keep the metered private key out of committed config files.

## What this fits — honestly

**A good fit:** internal document review, legal and compliance workflows, regulated industries, air-gapped networks, and teams whose policy forbids uploading documents to third-party processors.

**Not what this is:** a collaboration server. One stdio server serves one client process on one machine; annotations live in files, not in a shared database with presence and locking. Two people annotating the same document produce two files that you then merge with export/import — workable, but it is a merge, not live collaboration.

## FAQ

**Does any document content leave the machine?** Not from the server. Annotation text and previews you ask the agent to read travel in the conversation to your model provider.

**Does it need internet at runtime?** No — only to fetch the package or image at install time, and only when metered licensing is enabled.

**Can I run it air-gapped?** Yes. Pre-pull the image, use a license file rather than metered keys, and pin the version.

**What ports does it open?** None. stdio only.

**How do I prove that?** Run it and watch: no listening sockets, no outbound connections while annotating. The [verification script]({{< ref "annotation/net/mcp/troubleshooting.md" >}}#verifying-an-installation-end-to-end) performs a real handshake and a real engine call so you can observe exactly what happens.
