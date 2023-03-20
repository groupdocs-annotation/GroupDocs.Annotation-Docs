---
id: latest-release
url: annotation/net/latest-release
title: Latest Release (January 2023)
weight: 1
description: The latest release notes for the most up to date GroupDocs.Annotation version
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---

## Full list of changes in this release

| Key | Category | Summary |
| --- | --- | --- |
| ANNOTATIONNET-2147 | Feature | [Added an ability to set a FontSize property for ReplacementAnnotation](#added-ability-to-set-fontsize-property-for-replacementannotation) |
| ANNOTATIONNET-2156 | Fix  | Fixed the broken link at the end of [SquigglyAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/squigglyannotation/) page |


## Major Features

### Added ability to set FontSize property for ReplacementAnnotation
In this release we've implenented [IFontSize](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels.interfaces.properties/ifontsize/) interface for [IReplacementAnnotation](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels.interfaces.annotations/ireplacementannotation/). From user perspective, it means that from now there is an ability to set a font size for replacement annotation.

With the replacement annotation you are allowed to replace text on the document to any other text you want. With the v23.1 you are also allowed to specify the FontSize of the new text. Here is a small code snippet that demonstrate how you can achieve this:

{{< tabs "example">}}
{{< tab "C#" >}}
```cs
using (Annotator annotator = new Annotator("input.pdf"))
{
    ReplacementAnnotation replacement = new ReplacementAnnotation
    {
	    FontSize = 50,
	    // other propeties
    };
    annotator.Add(replacement);
    annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}

The following image demonstrates the result:

![](/annotation/net/images/groupdocs-annotation-for-net-23-1-release-notes-font-size-difference.png)

Learn more about replacement annotation and it's other features here: [ReplacementAnnotation](https://docs.groupdocs.com/annotation/net/add-replacement-annotation/)