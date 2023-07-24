---
id: installation
url: annotation/java/installation
title: Installation
weight: 4
description: ""
keywords:
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:
        name: How to installation GroupDocs.Annotation for annotate docs in Java
        description: For annotate pdf, words, images, cells, slides and diagram need add to your project GroupDocs.Annotation via Maven.
        productCode: annotation
        productPlatform: java
toc: True
---

GroupDocs hosts all Java APIs on [GroupDocs Repository](https://releases.groupdocs.com/java/repo/). You use the [GroupDocs.Annotation for Java](https://releases.groupdocs.com/java/repo/com/groupdocs/groupdocs-annotation/) API directly in your Maven projects with simple configurations.

### Specify GroupDocs Repository Configuration

First, you need to specify GroupDocs repository configuration/location in your Maven `pom.xml` as follows: 

{{< tabs "example1">}}
{{< tab "XML" >}}
```xml
<repositories>
    <repository>
        <id>GroupDocsJavaAPI</id>
        <name>GroupDocs Java API</name>
        <url>http://repository.groupdocs.com/repo/</url>
    </repository>
</repositories>
```
{{< /tab >}}
{{< /tabs >}}

### Define GroupDocs.Annotation for Java API Dependency

Then define GroupDocs.Annotation for Java API dependency in your `pom.xml` as follows:

{{< tabs "example2">}}
{{< tab "XML" >}}
```xml
<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>23.6</version> 
    </dependency>
</dependencies>
```
{{< /tab >}}
{{< /tabs >}}
