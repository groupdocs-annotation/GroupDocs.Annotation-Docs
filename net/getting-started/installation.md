---
id: installation
url: annotation/net/installation
title: Installation
weight: 4
description: "The page describes how to add the GroupDocs.Annotation library to your .NET project."
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---
This topic describes how to add the GroupDocs.Annotation library to your .NET project. You can use a NuGet package to install this library or you can download necessary DLLs from the GroupDocs website: [https://releases.groupdocs.com/annotation/net/](https://releases.groupdocs.com/annotation/net/).

## Install GroupDocs.Annotation using NuGet packages

You can use the following tools to install the [GroupDocs.Annotation](https://www.nuget.org/packages/GroupDocs.Annotation) NuGet package: 

 * [NuGet Package Manager](#use-the-nuget-package-manager-in-visual-studio)
 * [Package Manager Console](#use-the-package-manager-console-in-visual-studio)
 * [.NET CLI](#use-the-net-cli)

### Use the NuGet Package Manager

Open your project or solution in Visual Studio and follow the steps below to install the **GroupDocs.Annotation** package using the [NuGet Package Manager](https://learn.microsoft.com/en-us/nuget/consume-packages/install-use-packages-visual-studio):

1. In **Solution Explorer**, right-click your project name and select **Manage NuGet Packages** to display the NuGet Package Manager.

    ![Manage NuGet packages in Visual Studio](/annotation/net/images/manage-nuget-packages.png)

2. Select the **Browse** tab and type **GroupDocs.Annotation** in the search box. Select the latest version of the **GroupDocs.Annotation** package and click **Install**.

    ![](/annotation/net/images/install-nuget-package.png)

### Use the Package Manager Console

The [Package Manager Console](https://learn.microsoft.com/en-us/nuget/consume-packages/install-use-packages-powershell) uses PowerShell commands to install, update, and remove NuGet packages. Open your project in Visual Studio and click **Tools** -> **NuGet Package Manager** -> **Package Manager Console** to open the console window. Run the the following command to install the latest version of the **GroupDocs.Annotation** library:

{{< tabs "example1">}}
{{< tab "PowerShell" >}}
```
PM> Install-Package GroupDocs.Annotation
```
{{< /tab >}}
{{< /tabs >}}

![Use Package Manager Console ](/annotation/net/images/package-manager-console.png)

### Use the .NET CLI

You can also use the [.NET CLI tool](https://docs.microsoft.com/en-us/dotnet/core/tools/) to install and update NuGet packages. Open a terminal in your project's folder and execute the following command to install the **GroupDocs.Annotation** package:

{{< tabs "example2">}}
{{< tab ".NET CLI" >}}
```
dotnet add package GroupDocs.Annotation
```
{{< /tab >}}
{{< /tabs >}}

## Download GroupDocs.Annotation from the official website

Visit [https://releases.groupdocs.com/annotation/net/](https://releases.groupdocs.com/annotation/net/) and download the **GroupDocs.Annotation** assemblies as a ZIP archive or MSI installer. To reference the downloaded assembly files in your project, do the following:

1. Extract files from the ZIP archive or run the MSI installer to install **GroupDocs.Annotation** to a specific location on your computer.
2. Open your solution or project in Visual Studio.
3. In **Solution Explorer**, right-click the **References** or **Dependencies** node, and select **Add Reference** (for a .NET Framework project) or **Add Project Reference** (for a .NET Core project).
4. In the **Reference Manager** dialog box, select the **Browse** tab and click **Browse** to locate the _GroupDocs.Annotation.dll_ file for the target framework.

    ![Browse for the GroupDocs.Annotation assembly](/annotation/net/images/browse-for-groupdocs-dll.png)

5. Click **OK** to add a reference to the **GroupDocs.Annotation** library to your project.

{{< alert style="warning" >}}
If your application targets .NET Core / .NET 5+, ensure that your project has all the required dependencies installed. Refer to the following page for details: [GroupDocs.Annotation dependencies](https://www.nuget.org/packages/groupdocs.annotation#dependencies-body-tab).
{{< /alert >}}
