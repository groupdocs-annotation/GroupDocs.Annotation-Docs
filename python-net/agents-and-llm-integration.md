---
id: agents-and-llm-integration
url: annotation/python-net/agents-and-llm-integration
title: AI agents and LLM integration
linkTitle: Agents and LLMs
weight: 6
description: "Use GroupDocs.Annotation for Python via .NET with AI coding assistants and LLMs — the bundled AGENTS.md reference, the GroupDocs MCP server, and machine-readable documentation."
keywords: AI agents, LLM, AGENTS.md, MCP, Claude, Cursor, Copilot, annotation, python
productName: GroupDocs.Annotation for Python via .NET
hideChildren: False
toc: True
---

GroupDocs.Annotation for Python via .NET is designed to work smoothly with AI coding assistants such as Claude Code, Cursor, and GitHub Copilot in agent mode.

## Built into the package

The `groupdocs-annotation-net` wheel ships a bundled `AGENTS.md` reference. Once the package is installed, AI tools discover it automatically at `groupdocs/annotation/AGENTS.md`. It covers the canonical imports, the open → add → save workflow, per-operation recipes, licensing, the full API-surface tables, and troubleshooting — everything an agent needs to write correct annotation code without guessing.

## MCP server

For on-demand documentation lookups, point your AI tool at the GroupDocs MCP server:

```json
{
  "mcpServers": {
    "groupdocs-docs": {
      "url": "https://docs.groupdocs.com/mcp"
    }
  }
}
```

This works with Claude Code (`~/.claude/settings.json`), Cursor (`.cursor/mcp.json`), VS Code Copilot (`.vscode/mcp.json`), and any MCP-compatible client.

## Machine-readable documentation

LLM-optimized documentation for retrieval-augmented generation and context loading is available at [`https://docs.groupdocs.com/annotation/python-net/llms-full.txt`](https://docs.groupdocs.com/annotation/python-net/llms-full.txt).

## AGENTS.md reference

The complete reference bundled inside the wheel is reproduced below.

````markdown
# GroupDocs.Annotation for Python via .NET -- AGENTS.md

> Instructions for AI agents working with this package.

Add, edit, and remove annotations and markup on documents and images -- area/ellipse/arrow/point/distance/polyline shapes, text highlight/underline/strikeout/squiggly, replacement and redaction markups, watermarks, image and link stamps, editable text fields, and threaded review comments (replies) -- then save back to the original format. Works across PDF, Word, Excel, PowerPoint, Visio, CAD, images, email, and more through one unified API, with no MS Office or external software installed.

## Install

```bash
pip install groupdocs-annotation-net
```

**Python**: 3.5 - 3.14 | **Platforms**: Windows, Linux, macOS

## Resources

| Resource | URL |
|---|---|
| Documentation | https://docs.groupdocs.com/annotation/python-net/ |
| LLM-optimized docs | https://docs.groupdocs.com/annotation/python-net/llms-full.txt |
| API reference | https://reference.groupdocs.com/annotation/python-net/ |
| Code examples | https://docs.groupdocs.com/annotation/python-net/developer-guide/ |
| Release notes | https://releases.groupdocs.com/annotation/python-net/release-notes/ |
| PyPI | https://pypi.org/project/groupdocs-annotation-net/ |
| Free support forum | https://forum.groupdocs.com/c/annotation/ |
| Temporary license | https://purchase.groupdocs.com/temporary-license |

## MCP Server

If your environment has MCP configured, you can connect your AI tool to the GroupDocs documentation server for on-demand API lookups:

```json
{
  "mcpServers": {
    "groupdocs-docs": {
      "url": "https://docs.groupdocs.com/mcp"
    }
  }
}
```

Works with Claude Code (`~/.claude/settings.json`), Cursor (`.cursor/mcp.json`), VS Code Copilot (`.vscode/mcp.json`), and any MCP-compatible client. If MCP is unavailable, fall back to the LLM-optimized docs URL above and this file -- both are shipped inside the wheel.

## Imports

```python
from groupdocs.annotation import Annotator, AnnotatorSettings, Document, FileType, License, Metered
from groupdocs.annotation.options import (
    AnnotationType, LoadOptions, SaveOptions,
)
from groupdocs.annotation.models import (
    Rectangle, Point, Reply, User, Role, PageInfo,
    BorderStyle, BoxStyle, HorizontalAlignment, VerticalAlignment, RotationDocument,
)
from groupdocs.annotation.models.annotation_models import (
    AnnotationBase,
    # shapes
    AreaAnnotation, ArrowAnnotation, DistanceAnnotation, EllipseAnnotation,
    PointAnnotation, PolylineAnnotation,
    # text markup
    HighlightAnnotation, UnderlineAnnotation, StrikeoutAnnotation, SquigglyAnnotation,
    ReplacementAnnotation, TextRedactionAnnotation, ResourcesRedactionAnnotation,
    # content
    WatermarkAnnotation, ImageAnnotation, LinkAnnotation, TextFieldAnnotation,
)
from groupdocs.pydrawing import Color   # use Color.<name>.to_argb() for ARGB ints
```

## Open + annotate + save (the core workflow)

`Annotator` is the entry point. The flow is always: **open → one or more `add(...)` calls → `save()`**. Each annotation is a plain object you configure with properties, then hand to `add`. Use `Annotator` as a context manager so the native document handle is released.

```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import AreaAnnotation
from groupdocs.pydrawing import Color

with Annotator("document.pdf") as annotator:
    area = AreaAnnotation()
    area.box = Rectangle(100, 100, 200, 80)        # x, y, width, height
    area.page_number = 0                            # 0-based page index
    area.background_color = Color.yellow.to_argb()  # ARGB int, NOT a Color object
    area.message = "Review this"
    annotator.add(area)
    annotator.save("annotated.pdf")
```

**`Annotator(...)` constructor.** `Annotator(file_path)` or `Annotator(stream)`, optionally with `LoadOptions` and/or `AnnotatorSettings`: `Annotator("doc.pdf", LoadOptions(password="..."))`, `Annotator(stream, LoadOptions(), AnnotatorSettings(...))`.

**`add(...)`** accepts a single annotation or a list of annotations. **`save(...)`** writes to a path or a writable stream; pass `SaveOptions` (as `save_options=...`) to control which annotation types and pages are rendered. By default `save()` renders all annotations onto the document.

**Coordinates & colors.** Geometry uses `Rectangle(x, y, width, height)` and `Point(x, y)` from `groupdocs.annotation.models`. **Colors are ARGB integers**, not `Color` objects — always pass `Color.<name>.to_argb()` (or a literal ARGB int) to `background_color`, `font_color`, `pen_color`, `underline_color`, and `squiggly_color`.

**Pages.** Annotation `page_number` is **0-based**, but `SaveOptions.first_page` / `last_page` are **1-based**.

## Operations

### Shape annotations (area / ellipse / arrow / point / distance / polyline)

```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Rectangle
from groupdocs.annotation.models.annotation_models import AreaAnnotation, EllipseAnnotation
from groupdocs.pydrawing import Color

area = AreaAnnotation()
area.box = Rectangle(100, 100, 200, 80)
area.background_color = Color.yellow.to_argb()   # ARGB int
area.pen_color = Color.red.to_argb()             # ARGB int
area.opacity = 0.7
area.page_number = 0
area.message = "Flagged region"

ell = EllipseAnnotation()
ell.box = Rectangle(50, 200, 120, 60)
ell.page_number = 0

with Annotator("document.pdf") as annotator:
    annotator.add([area, ell])     # add several at once
    annotator.save("annotated.pdf")
```

Shape types share `box`, `background_color` / `pen_color`, and `opacity`. `ArrowAnnotation`, `DistanceAnnotation`, and `PolylineAnnotation` use the same box/points surface; `PointAnnotation` anchors a comment at a single point.

### Text markup (highlight / underline / strikeout / squiggly / replacement)

```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.models import Point
from groupdocs.annotation.models.annotation_models import HighlightAnnotation
from groupdocs.pydrawing import Color

hl = HighlightAnnotation()
hl.font_color = Color.yellow.to_argb()
hl.page_number = 0
# Quad points around the target text (top-left, top-right, bottom-right, bottom-left):
hl.points = [Point(80, 730), Point(240, 730), Point(240, 750), Point(80, 750)]

with Annotator("document.pdf") as annotator:
    annotator.add(hl)
    annotator.save("highlighted.pdf")
```

Text-markup types expose `points` (a list of `Point` describing the marked region) and `font_color`; the rest of the markup family (`UnderlineAnnotation`, `StrikeoutAnnotation`, `SquigglyAnnotation`, `ReplacementAnnotation`, `TextRedactionAnnotation`, `ResourcesRedactionAnnotation`) follows the same shape.

### Review comments (replies)

```python
from groupdocs.annotation.models import Reply

r1 = Reply(); r1.comment = "Please double-check this"
r2 = Reply(); r2.comment = "Confirmed"

area.replies = [r1, r2]            # attach a comment thread to any annotation
```

`Reply` has `comment`, `user` (a `User`), `replied_on`, and `id`. A `User(id, name, role)` carries a `Role` (`VIEWER` / `EDITOR`).

### Content annotations (watermark / image / link / text field)

`WatermarkAnnotation`, `ImageAnnotation` (set `image_path`), `LinkAnnotation` (set `url`), and `TextFieldAnnotation` are created and added the same way — configure their properties, then `annotator.add(...)`.

### List, update, remove

```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.options import AnnotationType

with Annotator("annotated.pdf") as annotator:
    all_annotations = annotator.get()              # every annotation -> list
    areas = annotator.get(AnnotationType.AREA)     # filter by type -> list
    annotator.update(all_annotations[0])           # push a modified annotation back
    annotator.remove(all_annotations[0])           # by object, or annotator.remove(id)
    annotator.save("edited.pdf")
```

### Save options (page range + annotation-type filter)

```python
from groupdocs.annotation import Annotator
from groupdocs.annotation.options import SaveOptions, AnnotationType

with Annotator("document.pdf") as annotator:
    annotator.add(area)
    options = SaveOptions()
    options.annotation_types = AnnotationType.AREA   # render only area annotations
    options.first_page = 1                           # 1-based
    options.last_page = 2
    annotator.save("filtered.pdf", save_options=options)
```

### Document info

```python
with Annotator("document.pdf") as annotator:
    info = annotator.document.get_document_info()    # format, page count, size
    print(info.file_type.file_format, info.page_count, info.size)
```

### Save to a stream

```python
import io
with Annotator("document.pdf") as annotator:
    annotator.add(area)
    buf = io.BytesIO()
    annotator.save(buf)                # BytesIO is updated after save
    data = buf.getvalue()
```

## Licensing

```python
from groupdocs.annotation import License

# From file
License().set_license("path/to/license.lic")

# From stream
with open("license.lic", "rb") as f:
    License().set_license(f)
```

Or auto-apply: `export GROUPDOCS_LIC_PATH="path/to/license.lic"`

Metered licensing is also available:

```python
from groupdocs.annotation import Metered

Metered().set_metered_key("public-key", "private-key")
print(Metered().get_consumption_quantity(), Metered().get_consumption_credit())
```

**Evaluation vs licensed.** Without a license the library still runs and `save()` completes normally, but the output carries an evaluation watermark/banner (the output file is noticeably larger). There is no per-process document-open cap. Set `GROUPDOCS_LIC_PATH` (or call `License().set_license(...)`) and re-run to clear the watermark. A 30-day full license is free: https://purchase.groupdocs.com/temporary-license

## API Reference

### Annotator

| Method | Returns | Description |
|---|---|---|
| `Annotator(file_path / stream [, load_options [, settings]])` | | Open by path or binary stream; optional `LoadOptions` / `AnnotatorSettings`. Context manager. |
| `add(annotation)` / `add([annotations])` | `None` | Add one annotation or a list. |
| `update(annotation)` | `None` | Replace an existing annotation (matched by id). |
| `remove(annotation)` / `remove(id)` | `None` | Remove by object or by id; a list is also accepted. |
| `get()` | `list` | All annotations on the document. |
| `get(annotation_type)` | `list` | Annotations of one `AnnotationType`. |
| `save(path)` / `save(path, save_options=...)` / `save(stream)` | `None` | Render annotations and write the result. |
| `dispose()` | `None` | Release native resources (handled by `with`). |

`Annotator` properties: `document` (`Document` — `get_document_info()`), `rotation`, `process_pages`. `AnnotatorSettings` carries `logger` / `cache`.

### Annotation types (`groupdocs.annotation.models.annotation_models`)

| Type | Notes |
|---|---|
| `AreaAnnotation`, `EllipseAnnotation` | `box` (`Rectangle`), `background_color`, `pen_color`, `opacity` (ARGB-int colors). |
| `ArrowAnnotation`, `DistanceAnnotation`, `PolylineAnnotation` | Line/shape markups; box + points. |
| `PointAnnotation` | A single comment anchor at a point. |
| `HighlightAnnotation`, `UnderlineAnnotation`, `StrikeoutAnnotation`, `SquigglyAnnotation` | Text markup; `points` (quad) + `font_color`. |
| `ReplacementAnnotation`, `TextRedactionAnnotation`, `ResourcesRedactionAnnotation` | Replace / redact text or resources. |
| `WatermarkAnnotation` | Text watermark stamp. |
| `ImageAnnotation` | Image stamp (`image_path`). |
| `LinkAnnotation` | Hyperlink over a region (`url`). |
| `TextFieldAnnotation` | Editable text field. |
| All | Inherit `id`, `message`, `page_number`, `replies`, `created_on`, `user`, `type` from `AnnotationBase`. |

### Options, models & enums

| Type | Notes |
|---|---|
| `LoadOptions(password=...)` | Open protected input. |
| `SaveOptions` | `annotation_types`, `first_page` (1-based), `last_page`, `only_annotated_pages`. |
| `AnnotationType` | Enum of annotation kinds (filter for `get(...)` / `SaveOptions`). |
| `Rectangle(x, y, width, height)` / `Point(x, y)` | Geometry (from `...models`). |
| `Reply` | `comment`, `user`, `replied_on`, `id`. |
| `User(id, name, role)` / `Role` | `VIEWER`, `EDITOR`. |
| `BorderStyle`, `BoxStyle`, `HorizontalAlignment`, `VerticalAlignment`, `RotationDocument` | Styling enums. |

### License / Metered

`License().set_license(path_or_stream)` · `Metered().set_metered_key(public, private)` · `Metered().get_consumption_quantity()` · `Metered().get_consumption_credit()`

## Key Patterns

- **Properties**: use `snake_case` -- auto-mapped to .NET `PascalCase`
- **Context managers**: `with Annotator(...) as a:` ensures the document handle is released
- **Build then add**: construct an annotation object, set its properties, then `add(it)` — or `add([...])` for several
- **Colors are ARGB ints**: always pass `Color.<name>.to_argb()` (e.g. `annotation.background_color = Color.yellow.to_argb()`), never a `Color` object
- **Geometry**: `Rectangle(x, y, width, height)`, `Point(x, y)`; text markup uses a `points` quad
- **Pages**: annotation `page_number` is **0-based**; `SaveOptions.first_page` / `last_page` are **1-based**
- **Replies**: attach a `list[Reply]` to any annotation's `replies` for review comments
- **Streams**: pass `open("file", "rb")` or `io.BytesIO(data)` where .NET expects a Stream; `BytesIO` is updated after `save(stream)`
- **Enums**: case-insensitive, lazy-loaded (e.g., `AnnotationType.AREA`, `Role.EDITOR`)

## Platform Requirements

| Platform | Requirements |
|---|---|
| Windows | None |
| Linux | `apt install libgdiplus libfontconfig1 ttf-mscorefonts-installer` |
| macOS | `brew install mono-libgdiplus` |

## Troubleshooting

**Evaluation watermark on output** -- no license. Apply one with `License().set_license(...)` or set `GROUPDOCS_LIC_PATH`; a free 30-day license is at https://purchase.groupdocs.com/temporary-license

**Password-protected source** -- the input is encrypted. Open it with `Annotator(path, LoadOptions(password="..."))`.

**Unsupported or damaged file** -- the format isn't supported or the file is corrupted. Check it against the supported-formats list.

**`System.Drawing.Common is not supported`** -- install libgdiplus: `sudo apt install libgdiplus` (Linux) / `brew install mono-libgdiplus` (macOS)

**`Gdip` type initializer exception** -- outdated libgdiplus: `brew reinstall mono-libgdiplus` (macOS)

**Garbled text / missing fonts** -- install fonts: `sudo apt install ttf-mscorefonts-installer fontconfig && sudo fc-cache -f`

**`DllNotFoundException: libSkiaSharp`** -- stale system copy conflicts with bundled version. Rename it: `sudo mv /usr/local/lib/libSkiaSharp.dylib /usr/local/lib/libSkiaSharp.dylib.bak`

**`DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` errors** -- do NOT set this. Install ICU: `sudo apt install libicu-dev`

**`TypeLoadException`** -- reinstall: `pip install --force-reinstall groupdocs-annotation-net`

**Still stuck?** Post your question at https://forum.groupdocs.com/c/annotation/ -- the development team responds directly.
````
</content>
