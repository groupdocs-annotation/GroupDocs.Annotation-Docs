---
id: how-to-run-examples
url: annotation/net/how-to-run-examples
title: How to Run Examples
weight: 6
description: Examples to annotate on your documents, images or web pages using C#.
keywords: to annotate, annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
toc: True
---
{{< alert style="warning" >}}Before running an example make sure that GroupDocs.Annotation has been installed successfully.{{< /alert >}}

We offer multiple solutions on how you can run GroupDocs.Annotation examples, by building your own or using our back-end or front-end examples out-of-the-box.

## Build project from scratch

To build a project from scratch, follow these steps:

1.   Open Visual Studio and navigate to **File** -> **New **\->** Project**.
2.   Select the appropriate project type - Console App, ASP.NET Web App etc.
3.   Install **GroupDocs.Annotation for .NET** from NuGet or official GroupDocs website as described in the [guide]({{< ref "annotation/net/getting-started/installation.md" >}}).
4.   Develop the application using **GroupDocs.Annotation for .NET** like this:
{{< tabs "example1">}}
{{< tab "C#" >}}  
```csharp
// Create list of annotations
List<AnnotationBase> annotations = new List<AnnotationBase>()
{
    new AreaAnnotation()
    {
        PageNumber = 0,
        Box = new Rectangle(100, 100, 100, 100),
        Message = "area"
    },
                
    new EllipseAnnotation()
        {
            PageNumber = 0,
            Box = new Rectangle(200, 200, 80, 80),
            Message = "ellipse"
        }
};

// Create annotator
using  (Annotator annotator = new Annotator("C:\output\input.pdf"))
{
    // Add annotations
    annotator.Add(annotations);
    // Save result to "C:\output\result.pdf"
    annotator.Save("C:\output\result.pdf", new SaveOptions());
}
```
{{< /tab >}}
{{< /tabs >}}    
5.   Build and run your project. 
6.   Rendered document pages appears in the `C:\\output\\` directory.

## Run back-end examples

You can find the complete package of the **GroupDocs.Annotation** examples on [GitHub](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET). You can either [download the ZIP file](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET/archive/master.zip) or clone the GitHub repository using your any git client.  
If you downloaded the ZIP file, extract the folders to the local disk. The extracted files and folders look as follows:

![](/annotation/net/images/how-to-run-examples.png)

Find the CSharp solution file. The project is created in **Microsoft Visual Studio 2019**. The `Resources` folder contains all the sample documents and images used in the examples.  
To run the examples, open the solution file with Visual Studio and build the project. If needed, add missing references of GroupDocs.Annotation. All the functions are called in the **RunExamples.cs** file. Uncomment the function(s) you want to run and comment the rest.

![](/annotation/net/images/how-to-run-examples_1.png)

## Run MVC examples

To run the [GroupDocs.Annotation for .NET MVC Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC), follow these steps:

1.   Download the [source code](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC/archive/master.zip) from GitHub or clone the repository: 
{{< tabs "example2">}}
{{< tab "Git" >}} 
```bash
git clone https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC
{{< /tab >}}
{{< /tabs >}}  
2.   Open solution with the Visual Studio. Update common parameters in **web.config** and example related properties in **configuration.yml** to meet your requirements.  
3.   Open [http://localhost:8080/annotation](http://localhost:8080/annotation) in your favorite browser.

For details about project configuration please refer to this [guide](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC#configuration).

## Run WebForms examples

To run the [GroupDocs.Annotation for .NET Web.Forms Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms), follow these steps:

1.   Download [the source code](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms/archive/master.zip) from GitHub or clone this repository:
{{< tabs "example3">}}
{{< tab "Git" >}} 
```bash
git clone https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms.git
```
{{< /tab >}}
{{< /tabs >}}  
2.   Open solution with the Visual Studio. Update common parameters in **web.config** and example related properties in the **configuration.yml** to meet your requirements.
3.   Open [http://localhost:8080/annotation](http://localhost:8080/annotation) in your favorite browser.
For details about project configuration please refer to this [guide](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms#configuration).

## Run from Docker

Use the [Docker](https://www.docker.com/) image to try GroupDocs.Annotation for .NET features. Execute the following commands to run GroupDocs.Annotation for .NET from docker image:
{{< tabs "example4">}}
{{< tab "PowerShell" >}}
```
mkdir DocumentSamples
mkdir Licenses
docker run -p 8080:8080 --env application.hostAddress=localhost -v `pwd`/DocumentSamples:/home/groupdocs/app/DocumentSamples -v `pwd`/Licenses:/home/groupdocs/app/Licenses groupdocs/annotation
## Open http://localhost:8080/annotation in your favorite browser.
```
{{< /tab >}}
{{< /tabs >}}

## Contribute

If you want to add or improve an example, we encourage you to contribute to the project. All examples in this repository are open source and can be freely used in your applications.

To contribute, fork the repository, edit the code and create a pull request. We will review the changes and include it in the repository if found helpful.
