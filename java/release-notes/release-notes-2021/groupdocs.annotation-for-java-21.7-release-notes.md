---
id: groupdocs-annotation-for-java-21-7-release-notes
url: annotation/java/groupdocs-annotation-for-java-21-7-release-notes
title: GroupDocs.Annotation for Java 21.7 Release Notes
weight: 3
description: ""
keywords: 
productName: GroupDocs.Annotation for Java
hideChildren: False
---
{{< alert style="info" >}}
This page contains release notes for GroupDocs.Annotation for Java 21.7
{{< /alert >}}{{< alert style="danger" >}}
Breaking changes
In this version we're introducing new public API which was designed to be simple and easy to use. For more details about new API please check [Migration Notes]({{< ref "annotation/java/developer-guide/migration-notes.md" >}}) and [Developer Guide](https://docs.groupdocs.com/display/annotationjava/Developer+Guide) sections.
{{< /alert >}}

## Major Features
In this version Below the list of most notable changes in release of GroupDocs.Annotation for Java 21.7:
*   Legacy API was removed from product
*   Fixed several bugs and issues 
*   Added new type of annotation - Image Annotation for (SpreadSheet, Diagrams, Images, PDF, WordProcessing, Presentations)
*   Investigated and fixed coordinates of annotations to make them same on images preview as on documents for number of formats (PDF, Cells, Slides, Words)
*   Adding showing distance value for Distance annotations in different formats (Slides, PDF, Images, Diagrams, Cells)
*   Fixed Background color for highlight annotation is not set in Images
*   Implemented ability to add Image Annotations to Diagrams
*   Added overloads for Remove method
*   Implement image extracting of ImageAnnotation 
*   Fixed support DWG files
*   Fixed issue with encrypted SpreadSheet(Cells) files
*   Added new feature for managing different versions of annotated documents (supported formats: Words, PDF, PowerPoint and Open Document format presentations, Excel and Open Document format spreadsheets)
*   Added advanced rendering options for show\\hide replies
*   Added to new API getting pages image size
*   Fixed issue with throwing exception for encrypted Excel spreadsheets
*   Fixed cleanup replies for PowerPoint presentations
*   Annotation available in document after removing
*   Issue with generating preview for password-protected document
*   Issue with error when processing images
*   Implemented managing different versions of annotated documents for Images and Diagrams
*   Implemented additional overloads for Save method without filestream
*   Fixed background opacity for PNG files
*   Fixed issue with PagesInfo for Excel files in MVC project
*   Fixed clearing comments for Excel files
*   Fixed unable to Save document as file that was used to create annotator
*   Implemented Angle property for Image Annotation
*   Implemented horizontal and vertical alignment for Watermark
*   Implemented text horizontal alignment for TextField
*   Fixed saving only specific annotation types for html, email, words and image
*   Improved exceptions usage
*   Fixed incorrect position of text annotations types in Cells
*   Improved adding annotations to TIFF Images
*   Improved annotating images mechanism (optimized performance)
*   Added Equals operator for comparing Annotations
*   Fixed issue with open CAD files
*   Fixed failed to import annotations that was added on older versions (added backward compatibility)
*   Fixed issue with ImageData is not saving on Image annotation
*   Fixed restoring image from ImageData
*   Improved adding ImageAnnotation functionality
*   Fixed exception while processing specific xlsx files
*   Fixed exception while annotating email files
*   Fixed issue with streams when Save method invoked
*   Fixed Replacement annotation on Words files
*   Improve annotating PDF functionality by separating PdfCommentator to smaller classes and refactoring it
*   Fixed Index was out of range exception for specific Diagrams 
*   Fixed issues with opening big Spreadsheet documents
*   Fixed issues with saving document as an image
*   Fixed Object reference not set to an instance of an object for specific CAD files
*   Implemented generating of specified worksheet columns for the Cells format
*   Improved Cells generating preview by splitting the worksheet into multiple images
*   Fixed Empty PagesInfo in specific diagram file
    
## Full List of Issues Covering all Changes in this Release
| Key | Summary | Issue Type |
| --- | --- | --- |
| ANNOTATIONNET-1421 | Implement horizontal text alignment TextField and TextWatermark annotations | Feature |
| ANNOTATIONNET-1292 | Implement managing different versions of annotated documents for Diagrams | Feature |
| ANNOTATIONNET-1291 | Implement managing different versions of annotated documents for Images | Feature |
| ANNOTATIONNET-884 | Implement ability to add Image annotation to Diagrams | Feature |
| ANNOTATIONNET-880 | Implement ability to add Image annotation to PDF | Feature |
| ANNOTATIONNET-881 | Implement ability to add Image annotation to SpreadSheet | Feature |
| ANNOTATIONNET-882 | Implement ability to add Image annotation to Presentations | Feature |
| ANNOTATIONNET-883 | Implement ability to add Image annotation to WordProcessing | Feature |
| ANNOTATIONNET-1220 | Implement ability to add Image annotation to Images | Feature |
| ANNOTATIONNET-816 | Managing different versions of annotated file | Feature |
| ANNOTATIONNET-1537 | Investigate the way of displaying huge worksheets of Spreadsheet | Improvement |
| ANNOTATIONNET-1482 | Replace file ImageAnnotation functionality with streams | Improvement |
| ANNOTATIONNET-1418 | Improve adding annotations to TIFF Images | Improvement |
| ANNOTATIONNET-1450 | Improve ImageAnnotationHelper | Improvement |
| ANNOTATIONNET-1452 | Add comparison operator (Equals) overload for Annotation Models | Improvement |
| ANNOTATIONNET-1427 | Improve CellsInfo method in DocumentInfoExtractor | Improvement |
| ANNOTATIONNET-1355 | Improve exceptions usage. | Improvement |
| ANNOTATIONNET-1396 | Improve PDF document annotation accuracy | Improvement |
| ANNOTATIONNET-1369 | Add overloads for Annotator.Save method without stream or filepath | Improvement |
| ANNOTATIONNET-1320 | Pages image size | Improvement |
| ANNOTATIONNET-1318 | Document advanced rendering modes and options support | Improvement |
| ANNOTATIONNET-1241 | Add overloads for Annotator Remove Method | Improvement |
| ANNOTATIONNET-1248 | Implement image extracting to ImageAnnotation | Improvement |
| ANNOTATIONNET-1135 | Investigate and fix coordinates discrepancy for Cells | Improvement |
| ANNOTATIONNET-1139 | Investigate and fix coordinates discrepancy for PDF | Improvement |
| ANNOTATIONNET-1140 | Investigate and fix coordinates discrepancy for Slides | Improvement |
| ANNOTATIONNET-1141 | Investigate and fix coordinates discrepancy for Words | Improvement |
| ANNOTATIONNET-1146 | Improve Words Shapes Import | Improvement |
| ANNOTATIONNET-1165 | Adding showing distance value for Distance annotations in different formats(Slides, PDF, Images, Diagrams, Cells) | Improvement |
| ANNOTATIONNET-1170 | Improve Logging in Cells | Improvement |
| ANNOTATIONNET-1171 | Improve Logging in Diagram | Improvement |
| ANNOTATIONNET-1172 | Improve Logging in Email/Html | Improvement |
| ANNOTATIONNET-1173 | Improve Logging in Images | Improvement |
| ANNOTATIONNET-1174 | Improve Logging in PDF | Improvement |
| ANNOTATIONNET-1175 | Improve Logging in Slides | Improvement |
| ANNOTATIONNET-1176 | Improve Logging in Words | Improvement |
| ANNOTATIONNET-1177 | Improve Logging in Common Classes | Improvement |
| ANNOTATIONNET-1484 | Split PdfCommentator functionality to improve annotating PDF | Improvement |
| ANNOTATIONNET-1514 | Incorrect image size for Excel document | Bug |
| ANNOTATIONNET-1540 | PagesInfo is empty | Bug |
| ANNOTATIONNET-1536 | Index was out of range. Must be non-negative and less than the size of the collection for Diagrams document | Bug |
| ANNOTATIONNET-1516 | Image saving failed | Bug |
| ANNOTATIONNET-1515 | Object reference not set to an instance of an object for CAD file. | Bug |
| ANNOTATIONNET-1513 | Index out of range on specific Diagrams document | Bug |
| ANNOTATIONNET-1490 | Cannot open Cells file | Bug |
| ANNOTATIONNET-1392 | Replacement annotation damages words file | Bug |
| ANNOTATIONNET-1485 | CorruptedOrDamagedFileException on opening xlsx files | Bug |
| ANNOTATIONNET-1486 | Method Annotator.Save returns closed stream | Bug |
| ANNOTATIONNET-1487 | Can't get document info for msg file | Bug |
| ANNOTATIONNET-1488 | NullReferenceException when annotating e-mail | Bug |
| ANNOTATIONNET-1457 | Cad file can't be opened | Bug |
| ANNOTATIONNET-1458 | Failed to import annotations that was added on older versions | Bug |
| ANNOTATIONNET-1460 | ImageData is not saving on Image annotation | Bug |
| ANNOTATIONNET-1461 | Restore image from ImageData | Bug |
| ANNOTATIONNET-1426 | Incorrect vertical position of the text annotations on Excel files. | Bug |
| ANNOTATIONNET-1425 | Exception 'Failed extract annotations from images' during removing annotations from PNG. | Bug |
| ANNOTATIONNET-1424 | Stream is used by another process after Images CleanUp |    Bug |
| ANNOTATIONNET-1415 | Corrupted or damaged file error | Bug |
| ANNOTATIONNET-1420 | Saving Html with Images throws exception | Bug |
| ANNOTATIONNET-1334 | Annotations available after removing. | Bug |
| ANNOTATIONNET-1335 | Error during generating preview for password-protected document. | Bug |
| ANNOTATIONNET-1336 | Unexpected error with message "The image file format may be not supported at the moment." for Jpg. | Bug |
| ANNOTATIONNET-1178 | FilteringAnnotationTypes example raised and exception | Bug |
| ANNOTATIONNET-1184 | Background color for highlight annotation is not set in Images | Bug |
| ANNOTATIONNET-1132 | Issue with one page PDF preview generating | Bug |
| ANNOTATIONNET-1133 | Wrong Slides preview generating | Bug |
| ANNOTATIONNET-1145 | Compatibility issues under .NET Standard 2.0 | Bug |
| ANNOTATIONNET-1103 | Issue with saving formats in Presentations | Bug |
| ANNOTATIONNET-1104 | Issue with Word Processing documents cleanup | Bug |
| ANNOTATIONNET-1106 | Issue with cleanup Link annotation on Presentations | Bug |
| ANNOTATIONNET-1219 | Example Code throws NullReferenceException for SpreadSheet | Bug |
| ANNOTATIONNET-1240 | Fix Dwg File Support | Bug |
| ANNOTATIONNET-1242 | Distance annotation was added in wrong place in jpg file | Bug |
| ANNOTATIONNET-1243 | Font color was changed after removing text redaction annotation | Bug |
| ANNOTATIONNET-1245 | Remove residual files after Image Annotation work | Bug |
| ANNOTATIONNET-1246 | Encrypted SpreadSheet(Cells) files throws exception | Bug |
| ANNOTATIONNET-1247 | Issue with AnnotationType byte Flag | Bug |
| ANNOTATIONNET-1257 | Exception while deleting work files when adding ImageAnntation | Bug |
| ANNOTATIONNET-1296 | Cannot access a closed Stream | Bug |
| ANNOTATIONNET-1284 | Encrypted Excel spreadsheet file throws exception | Bug |
| ANNOTATIONNET-1321 | CleanUp method for PowerPoint presentation does not remove replies | Bug |
| ANNOTATIONNET-1370 | Adding annotations to PNG image makes background non transparent | Bug |
| ANNOTATIONNET-1368 | Unable to Save document as file that was used to create annotator | Bug |
| ANNOTATIONNET-1367 | A generic error occurred in GDI+ when processing Slides documents | Bug |
| ANNOTATIONNET-1362 | TextAnnotations not cleaning in Cells after adding Versions | Bug |
| ANNOTATIONNET-1361 | Comments not cleaned in Excel files | Bug |
| ANNOTATIONNET-1358 | Wrong file metadata issue in Images after adding Versions | Bug |
| ANNOTATIONNET-1357 | Empty PagesInfo for Excel file in MVC project. | Bug |
| ANNOTATIONJAVA-1217 | Exception occurred while remove annotations from xls file | Bug |
| ANNOTATIONJAVA-1238 | Add DWG files support | Bug |
| ANNOTATIONJAVA-1240 | Remove underline annotation doesn't work | Bug |
| ANNOTATIONJAVA-1241 | Font color was changed after removing text redaction annotation | Bug |
| ANNOTATIONJAVA-1243 | Cannot add annotations to the image. | Bug |
| ANNOTATIONJAVA-1245 | Distance annotation in jpg file | Bug |
| ANNOTATIONJAVA-1312 | Remove annotation via AnnotationType.None dosen't work | Bug |
| ANNOTATIONJAVA-1311 | Error when save Text Redaction annotation to file | Bug |

## Public API and Backward Incompatible Changes

{{< alert style="info" >}}This section lists public API changes that were introduced in GroupDocs.Annotation for Java 21.7. It includes not only new and obsoleted public methods, but also a description of any changes in the behavior behind the scenes in GroupDocs.Annotation which may affect existing code. Any behavior introduced that could be seen as a regression and modifies existing behavior is especially important and is documented here.{{< /alert >}}

1.  **Add Image Annotation** 
    
    **Image annotation** allows to add image within document page like shown at the picture below.
    
    ![](annotation/java/images/groupdocs-annotation-for-net-20-1-release-notes.png)
        
    {{< alert style="info" >}}IMPORTANT: On version 20.1 Image Annotation supported only in PDF, Words, Slides, Cells, Images documents.{{< /alert >}}

    There is an ability to specify the next properties for ImageAnnotation type:
    *   ImagePath - defines image local or remote path. Warning, if you use remote path - you need to remove http and https protocol, or www if it present. This error is now investigating.

    **Not Correct:**
    [https://www.google.com.ua/images/branding/googlelogo/2x/googlelogo\_color\_92x30dp.png](https://www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png)
    [http://www.google.com.ua/images/branding/googlelogo/2x/googlelogo\_color\_92x30dp.png](http://www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png)

    **Correct:**
    [www.google.com.ua/images/branding/googlelogo/2x/googlelogo\_color\_92x30dp.png](http://www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png)
    [google.com.ua/images/branding/googlelogo/2x/googlelogo\_color\_92x30dp.png](http://www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png)

    *   Box - defines annotation position at document page; (image will be resized for your custom width and height)
    *   Opacity - allows to set annotation opacity (present in all supported formats, examples of it you can see above);

    Follow these steps to add Image annotation to document:

    *   Instantiate [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator) object with input document path or stream;
    *   Instantiate ImageAnnotation object with desired properties (position, page number, etc);
    *   Call [Add](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)) method and pass ImageAnnotation object;
    *   Call [Save](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()) method with resultant document path or stream.
        
    The following code demonstrates how to add ImageAnnotation with remote ImagePath to the document:
        
    ```java
    try (Annotator annotator = new Annotator("input.pdf")) {
        ImageAnnotation imageAnnotation = new ImageAnnotation();
        imageAnnotation.setBox(new Rectangle(100, 100, 100, 100));
        imageAnnotation.setOpacity(0.7);
        imageAnnotation.setPageNumber(0);
        imageAnnotation.setImagePath("www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png");
        imageAnnotation.setAngle(100.0);

        annotator.add(imageAnnotation);
        annotator.save("result.pdf");
    }
    ```
        
    The result would be
    ![](annotation/java/images/groupdocs-annotation-for-net-20-1-release-notes_1.png)
    
2.  **Added new overloads for Get method** 
    
    On version 20.2 was added new overload of Annotator.Get method. It allows to get list of annotation of specific type
    ```java
    try (Annotator annotator = new Annotator("annotated.pdf")) {
        List<AnnotationBase> tmp = annotator.get(AnnotationType.Area);
    }
    ```
    
3.  **Added new overloads for Remove method**  
    On version 20.2 Was added new overload of Annotator.Remove method.
    New overloads method allow to remove single Annotation or list of Annotations.
    Follow these steps to add annotation to document:
    
    *   Instantiate [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator) object with input document path or stream;
    *   Call [Remove](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#remove(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)) method and give them id, list of id's, annotation to delete, or list of annotations 
    *   Call [Save](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)) method to save changes
       
    1) Following code demonstrates overload how to remove Annotation from Document using annotation index:
    ```java
    try (Annotator annotator = new Annotator("result.xlsx")) {
        annotator.remove(0);
        annotator.save("removed.xlsx");
    }
    ```
    
    2) Following code demonstrates overload how to remove Annotation from Document using Annotation Object:
    ```java
    try (Annotator annotator = new Annotator("result.xlsx")) {
        List<AnnotationBase> tmp = annotator.get();
        annotator.remove(tmp.get(0));
        annotator.save("removed.xlsx");
    }
    ```
    
    3) Following code demonstrates overload how to remove some Annotations from Document using list of Id's:
    ```java
    try (Annotator annotator = new Annotator("result.xlsx")) {
        java.util.List<Integer> idList = new java.util.ArrayList<>();
        idList.add(0);
        idList.add(1);
        annotator.remove(idList);
        annotator.remove(idList);
        annotator.save("removed.xlsx");
    }
    ```

    4) Following code demonstrates how to remove some Annotations from Document using list of Annotations:
    ```java
    try (Annotator annotator = new Annotator("result.xlsx")) {
        List<AnnotationBase> tmp = annotator.get();
        annotator.removeInternal(tmp);
        annotator.save("removed.xlsx");
    }
    ```
4.  **Starting from version 21.7 several Save methods overloads was added for user convenience**  
    Now you can call Empty Save to save documents as input file for annotator. If you need to add some options, you may call Save method with only one parameter - SaveOptions, it will do the same as empty but will consider your options.

    1) Method accepts SaveOption parameter

    ```java
    try (Annotator annotator = new Annotator(_resultPath)) {
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setVersion(1);
        annotator.save(saveOptions);
    }
    ```

    2) Empty Save Method

    ```java
    try (Annotator annotator = new Annotator(_resultPath)) {
        annotator.save();
    }
    ```

5.  **From this time Annotation Models overload the standard Equals method and also implement the IEquatable interface with the type of the class from which this method is called.**
    Example how to use it:

    ```java
    try (Annotator annotator = new Annotator("annotated_file.pdf")) {
        List<AnnotationBase> annotations = annotator.get();
        ImageAnnotation imageAnnotation = new ImageAnnotation();
        imageAnnotation.setBox(new Rectangle(100, 100, 100, 100));
        imageAnnotation.setOpacity(0.7);
        imageAnnotation.setPageNumber(0);
        imageAnnotation.setImagePath("www.google.com.ua/images/branding/googlelogo/2x/googlelogo_color_92x30dp.png");
        imageAnnotation.setAngle(100.0);

        annotator.add(imageAnnotation);
        annotator.save("result.pdf");

        for(int i = 0; i < annotations.size(); i++) {
            if (imageAnnotation.equals(annotations.get(i))) {
                    // Do some stuff here...
            }
        }
    }
    
6.  **Removed the deprecated ImportAnnotations property from the LoadOptions class because annotations are imported automatically.**
    So, if before version 21.7 this code was correct:

    ```java
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setPassword("password");
    loadOptions.setImportAnnotations(true);
    try (Annotator annotator = new Annotator("input.pdf", loadOptions)) {}
    ```
    #
    Beginning with version 21.7, LoadOptions no longer has the ImportAnnotations property. The previous code needs to be changed. Example:


    ```java
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setPassword("password");
    try (Annotator annotator = new Annotator("input.pdf", loadOptions)) {}
    ```
7.  **New [WorksheetColumns](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/PreviewOptions#getWorksheetColumns()) property in [PreviewOptions](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.pagepreview/PreviewOptions) class that allows to specify the range of generated columns on a specified worksheet.**

    Example how to use it:
    ```java
    PreviewOptions previewOptions = new PreviewOptions(new CreatePageStream() {
        @Override
        public OutputStream invoke(int pageNumber) { //Stream => InputStream
            String pagePath = "/result_{pageNumber}.png";
            return File.create(pagePath).toOutputStream();
        }
    });

    previewOptions.getWorksheetColumns().add(new WorksheetColumnsRange("Sheet1", 2, 3));
    previewOptions.getWorksheetColumns().add(new WorksheetColumnsRange("Sheet1", 1, 1));

    try (Annotator annotator = new Annotator("input.xlsx")) {
        annotator.getDocument().generatePreview(previewOptions);
    }
    ```
    
    
8. **Versions of Annotated files**

    Every Time you Save file using Annotator.Save() method - you implicitly create a new version of the annotated file. Versions List stores not document, it keeps annotations that you add, remove, and change. So you can easy swap between different changes made with GroupDocs.Annotation. And of course you can set your version names. More information about how it works you can find in child Pages

    By default, they are created using unique GUID keys. Next, each aspect of using versions will be considered. The API execution logic has not changed, so you do not need to change your code to use it as before. By default, the latest version is loaded without your fate (that is, you will not notice the difference with previous releases). 

    1) Backward Compatibility

    The update is fully compatible with previous and next updates (The latest saved version will be used), however, using versions on previous versions is not possible and the list of versions in this document will not be changed. And If you update file from 20.4+ using 20.2 and lower few times, after loading this document on 20.4+ only last changes will be added as new version.

    2) Add Version with custom name

    If you want to swap between versions easily you might need to have ability to set custom versions names.

    Here the code that demonstrates how to save version with custom name:
    ```java
    try (Annotator annotator = new Annotator("input.pdf")) {
        AreaAnnotation areaAnnotation = new AreaAnnotation();
        areaAnnotation.setBox(new Rectangle(100, 100, 100, 100));
        annotator.update(areaAnnotation);
        SaveOptions saveOptions = new SaveOptions();
        saveOptions.setVersion("CUSTOM_VERSION" );
        annotator.save("result.pdf", saveOptions);
    }
    ```
    {{< alert style="info" >}}Version Property type is object, so it support any type, and you can use any variable as version variable{{< /alert >}}

    3) Get List of All version keys on a document

    If you don't know what versions were added earlier or want to know versions count
    Here the code that demonstrates how to get list of versions keys:
    ```java
    try (Annotator annotator = new Annotator("result.pdf")) { 
        List<Object> versionKeys = annotator.getVersionsList();
    }
    ```
    {{< alert style="info" >}}Annotator.GetVersionList() returns list of objects because it supports any type of key. But if you used some specified keys as string - you can convert it.{{< /alert >}}

    4) Get List of Annotations using version key

    If you need to get List of Annotations you can use Annotator.GetVersion() method
    Here code that demonstrates how to get list of annotations from individual version
    ```java
    try (Annotator annotator = new Annotator("result.pdf")) { 
        List<AnnotationBase> versionKeys = annotator.getVersion("CUSTOM_VERSION");
    }
    ```

    {{< alert style="info" >}}GetVersion method supports any type, and you can use any variable as version variable.{{< /alert >}}

    5) Load Document of custom Version

    Using LoadOptions.Version you can load previous versions of annotated document.
    Here the code that demonstrates how load version using version name:

    ```java
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setVersion("CUSTOM_VERSION");
    try (Annotator annotator = new Annotator("input.pdf", loadOptions)) {
        annotator.save("result_loaded.pdf");
    }
    ```

    {{< alert style="info" >}}Version Property type is object, so it support any type, and you can use any variable as a version.{{< /alert >}}

9. **Added RenderComments Property to PreviewOptions**
    If you need not to generate comments on image preview you may use *RenderComments* property

    {{< alert style="info" >}}This feature is only supported for Word processing documents.{{< /alert >}}

    Default value is *true*. If it is not needed to display replies and comments at the page preview - set *RenderComments* property to *false* (replies and comments still will be stored inside document).  
    Please notice, that *RenderComments* value will impact any document comments (doesn't matter if they were added by GroupDocs.Annotation or  some other application).
    Here the code that demonstrates how display image preview without comments:

    ```java
    Annotator annotator = new Annotator("inputPath");
    PreviewOptions previewOptions = new PreviewOptions(new CreatePageStream() {
        @Override
        public OutputStream invoke(int pageNumber) {
            String pagePath = resultPath.replace("result.pdf", "/result_{pageNumber}.png");
            return File.create(pagePath).toOutputStream();
        }
    })
    previewOptions.setPreviewFormat(PreviewFormats.PNG);
    previewOptions.setRenderComments(false);
    annotator.getDocument().generatePreview(previewOptions);
    ```

10. **Add PagesInfo property to IDocumentInfo**
    *PagesInfo* represents list of *PageInfo* objects which store information about each page.

    Now *PageInfo* have two properties - *Width* and *Height* in pixels. This properties works with all formats except Email And Html that doesn't have height and width so the won't store them and will be empty. All pages width and height will be same in all formats except Cells, so you can use size of first element as size of all document.

    Here code that demonstrates how to get Document width and Height:

    ```java
    Annotator annotator = new Annotator("input.docx");
    IDocumentInfo info = annotator.getDocument().getDocumentInfo();
    int width = info.getPagesInfo().get(0).getWidth();
    int height = info.getPagesInfo().get(0).getHeight();
    ```

11. **Added Angle property for ImageAnnotation**
    To set a custom angle for ImageAnnotation, you can use the new *Angle* property. Angle is measured in degrees.

    Example how to use it:

    ```java
    ImageAnnotation imageAnnotation = new ImageAnnotation();   
    imageAnnotation.setBox(new Rectangle(100, 100, 100, 100));
    imageAnnotation.setOpacity(0.7);
    imageAnnotation.setPageNumber(0);
    imageAnnotation.setImagePath("image.png");
    imageAnnotation.setAngle(90.0);
    ```

12. **Added horizontal and vertical alignment for Watermark**
    To set Horizontal and Vertical Alignments for WatermarkAnnotation, you can use Alignment properties.

    ```java
    WatermarkAnnotation watermarkAnnotation = new WatermarkAnnotation();
    watermarkAnnotation.setVerticalAlignment(VerticalAlignment.Bottom);
    watermarkAnnotation.setHorizontalAlignment(HorizontalAlignment.Left);
    ```


13. **Added text horizontal alignment for TextField**
    To set a text horizontal alignment you can use the TextHorizontalAlignment property.

    ```java
    TextFieldAnnotation textFieldAnnotation = new TextFieldAnnotation();
    textFieldAnnotation.setTextHorizontalAlignment(HorizontalAlignment.Left);
    ```