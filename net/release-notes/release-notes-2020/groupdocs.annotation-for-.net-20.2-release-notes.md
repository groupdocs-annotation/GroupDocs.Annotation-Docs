---
id: groupdocs-annotation-for-net-20-2-release-notes
url: annotation/net/groupdocs-annotation-for-net-20-2-release-notes
title: GroupDocs.Annotation for .NET 20.2 Release Notes
weight: 110
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 20.2{{< /alert >}}

## Major Features

Below is the list of most notable changes in release of GroupDocs.Annotation for .NET 20.2:
*   Implemented ability to add Image Annotations to Diagrams
*   Added overloads for Remove method
*   Implement image extracting of ImageAnnotation 
*   Fixed support DWG files
*   Fixed issue with encrypted SpreadSheet(Cells) files

## Full List of Issues Covering all Changes in this Release

| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-884 | Implement ability to add Image annotation to Diagrams | Feature |
| ANNOTATIONNET-1241 | Add overloads for Annotator Remove Method | Improvement |
| ANNOTATIONNET-1248 | Implement image extracting to ImageAnnotation | Improvement |
| ANNOTATIONNET-1240 | Fix Dwg File Support | Bug |
| ANNOTATIONNET-1242 | Distance annotation was added in wrong place in jpg file | Bug |
| ANNOTATIONNET-1243 | Font color was changed after removing text redaction annotation | Bug |
| ANNOTATIONNET-1245 | Remove residual files after Image Annotation work | Bug |
| ANNOTATIONNET-1246 | Encrypted SpreadSheet(Cells) files throws exception | Bug |
| ANNOTATIONNET-1247 | Issue with AnnotationType byte Flag | Bug |
| ANNOTATIONNET-1257 | Exception while deleting work files when adding ImageAnntation | Bug |
  

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for .NET 20.2. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

1.  **Extract Image from Image Annotation**  
    
    Added new method that allows to get image (.NET class *System.Drawing.Image*) from annotated Document 
    
    Follow these steps to Extract Image:
    *   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
    *   Call [Get](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/get) method and get annotations list
    *   Call GetImage method from some of [ImageAnnotations](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/imageannotation) from annotations list
    *   [Save](https://docs.microsoft.com/en-us/dotnet/api/system.drawing.image.save?view=netframework-4.8#System_Drawing_Image_Save_System_String_) image if it needed using Save Method. You can also use Property ImageExtension of [ImageAnnotation](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/imageannotation) to set correct image extension
    
    The following code demonstrates how to get image from Image Annotation:
    
    ```csharp
    using (Annotator annotator = new Annotator("result.xlsx"))
    {
      	var tmp = annotator.Get(AnnotationType.Image);
        ImageAnnotation img = tmp[0] as ImageAnnotation; 	
    	img.GetImage().Save($"res.{img.ImageExtension}");
    }
    ```
    
2.  **Added new overloads for Get method** 
    
    On version 20.2 was added new overload of Annotator.Get method. It allows to get list of annotation of specific type
    ```csharp
    using (Annotator annotator = new Annotator("annotated.pdf"))
    {
    	//List with only Annotations with type Area will be returned and saved as tmp variable                
    	var tmp = annotator.Get(AnnotationType.Area);            
    }
    ```
    
3.  **Added new overloads for Remove method**  
    On version 20.2 Was added new overload of Annotator.Remove method.
    New overloads method allow to remove single Annotation or list of Annotations.
    Follow these steps to add annotation to document:
    
    *   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
    *   Call [Remove](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/remove) method and give them id, list of id’s, annotation to delete, or list of annotations 
    *   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.annotator/save/methods/2) method to save changes
       
    1) Following code demonstrates overload how to remove Annotation from Document using annotation index:
    ```csharp
    using (Annotator annotator = new Annotator("result.xlsx"))
    {
    	annotator.Remove(0);
    	annotator.Save("removed.xlsx");
    }
    ```
    
    2) Following code demonstrates overload how to remove Annotation from Document using Annotation Object:
    ```csharp
    using (Annotator annotator = new Annotator("result.xlsx"))
    {
    	var tmp = annotator.Get();
    	annotator.Remove(tmp[0]);
    	annotator.Save("removed.xlsx");
    }
    ```
    
    3) Following code demonstrates overload how to remove some Annotations from Document using list of Id’s:
    ```csharp
    using (Annotator annotator = new Annotator("result.xlsx"))
    {
    	var idList = new List<int>{1, 2, 3};
    	annotator.Remove(idList);
    	annotator.Save("removed.xlsx");
    }
    ```

    4) Following code demonstrates how to remove some Annotations from Document using list of Annotations:
    ```csharp
    using (Annotator annotator = new Annotator("result.xlsx"))
    {
    	var tmp = annotator.Get();
    	annotator.Remove(tmp);
    	annotator.Save("removed.xlsx");
    }
    ```