---
id: system-requirements
url: annotation/python-net/system-requirements
aliases:
    - /annotation/python-net/getting-started/system-requirements/
title: System Requirements
linkTitle: System Requirements
weight: 6
description: "GroupDocs.Annotation for Python via .NET ships as a self-contained wheel and runs on Windows, Linux, and macOS without Microsoft Office, OpenOffice, or any other third-party software installed."
keywords: System Requirements, supported operating systems, supported python versions, groupdocs annotation python
productName: GroupDocs.Annotation for Python via .NET
hideChildren: False
toc: True
---

{{< alert style="info" >}}
GroupDocs.Annotation for Python via .NET operates independently of external software like Microsoft Word, Excel, PowerPoint, or Adobe Acrobat. To install it, simply follow one of the methods described in the [Installation](https://docs.groupdocs.com/annotation/python-net/installation/) section.
{{< /alert >}}

## Overview

GroupDocs.Annotation for Python via .NET does not require Microsoft Office, OpenOffice, Adobe Acrobat, or any other external software to be installed. The package is a self-contained wheel that bundles everything it needs, so the only prerequisites are a supported version of Python and the operating-system packages listed below.

## Supported Python Versions

GroupDocs.Annotation for Python via .NET supports the following Python versions:

* Python 3.5
* Python 3.6
* Python 3.7
* Python 3.8
* Python 3.9
* Python 3.10
* Python 3.11
* Python 3.12
* Python 3.13
* Python 3.14

## Supported Operating Systems

The package is distributed as a self-contained wheel that runs on the following platforms:

### Windows

* Windows x64

No additional dependencies are required on Windows.

### Linux

* Linux x64

On Linux you need to install a few system packages for graphics, fonts, and globalization:

```bash
apt install libgdiplus libfontconfig1 libicu-dev ttf-mscorefonts-installer
```

### macOS

* macOS x64 (Intel)
* macOS ARM64 (Apple Silicon)

On macOS install the graphics library via Homebrew:

```bash
brew install mono-libgdiplus
```

## No Third-Party Software Required

Unlike many document-processing tools, GroupDocs.Annotation for Python via .NET does not depend on Microsoft Office, OpenOffice, Adobe Acrobat, or any other application being installed on the machine. All loading, annotating, and saving of Word Processing documents, Spreadsheets, Presentations, PDFs, images, and the other [supported formats](https://docs.groupdocs.com/annotation/python-net/supported-document-formats/) is performed entirely by the bundled engine.
</content>
</invoke>
