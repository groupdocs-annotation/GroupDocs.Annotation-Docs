---
id: update-annotations
url: annotation/net/update-annotations
title: Update annotations
weight: 6
description: "Check this article and learn how to edit annotation properties - change annotation position, size, appearance etc. when annotate documents using GroupDocs.Annotation for .NET."
keywords: Update annotations, Edit annotation, Change annotation properties
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to get supported file formats info
        description: Learn how to get supported file formats step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of annotation class and specify the id of the annotation to be updated.
        - name: Parametrs annotation
          text: Pass new parametrs for annotation.
        - name: Update annotation to the document
          text: Call Annotator class .Update() method and pass the class name annotation.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/net) allows you to update annotations by specifying their [Id properties](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/annotationbase/properties/id). Also you can update  annotations by providing a collection of updated annotation objects that replaces all existing document annotations.  

To update annotations, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Create an [AnnotationBase](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/annotationbase) implementation and set Id of existed annotation (if annotation with that Id is not found, it is ignored) or path list of annotations (all existed annotations are removed).
3.   Call the [Update](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/update/index) method of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify annotations.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code demonstrates how to update annotations:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
            {
                AreaAnnotation original = new AreaAnnotation
                {
                    Id = 1,
                    BackgroundColor = 65535,
                    Box = new Rectangle(100, 100, 100, 100),
                    CreatedOn = DateTime.Now,
                    Message = "This is original annotation",
                    Replies = new List<Reply>
                    {
                        new Reply
                        {
                            Comment = "Original first comment",
                            RepliedOn = DateTime.Now
                        },
                        new Reply
                        {
                            Comment = "Original second comment",
                            RepliedOn = DateTime.Now
                        }
                    }
                };
                // add original annotation
                annotator.Add(original);
                annotator.Save("result.pdf");
            }

            // open annotated document
            using (Annotator annotator = new Annotator("result.pdf"))
            {
                //assuming we are going to change some properties of existing annotation
                AreaAnnotation updated = new AreaAnnotation
                {
                    // It's important to set existed annotation Id
                    Id = 1,
                    BackgroundColor = 255,
                    Box = new Rectangle(0, 0, 50, 200),
                    CreatedOn = DateTime.Now,
                    Message = "This is updated annotation",
                    Replies = new List<Reply>
                    {
                        new Reply
                        {
                            Comment = "Updated first comment",
                            RepliedOn = DateTime.Now
                        },
                        new Reply
                        {
                            Comment = "Updated second comment",
                            RepliedOn = DateTime.Now
                        }
                    }
                };
                // update annotation
                annotator.Update(updated);
                annotator.Save("result.pdf");
            }
```
{{< /tab >}}
{{< /tabs >}}

You can also update annotation using Id. You can also pass the list of annotations. In that case all previous annotations will be replaced by new list.

To do this, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Create an [AnnotationBase](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/annotationbase) implementation and set Id of existed annotation (if annotation with that Id is not found, it is ignored) or path list of annotations (all existed annotations will be removed).
3.   Call the [Update](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/update/index) method of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify annotations.
4.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code demonstrates how to update annotations using Id:

{{< tabs "example2">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
            {
                AreaAnnotation original = new AreaAnnotation
                {
                    Id = 1,
                    BackgroundColor = 65535,
                    Box = new Rectangle(100, 100, 100, 100),
                    CreatedOn = DateTime.Now,
                    Message = "This is original annotation",
                    Replies = new List<Reply>
                    {
                        new Reply
                        {
                            Comment = "Original first comment",
                            RepliedOn = DateTime.Now
                        },
                        new Reply
                        {
                            Comment = "Original second comment",
                            RepliedOn = DateTime.Now
                        }
                    }
                };
                // add original annotation
                annotator.Add(original);
                annotator.Save("result.pdf");
            }
 
            // open annotated document
            using (Annotator annotator = new Annotator("result.pdf"))
            {
                //assuming we are going to change some properties of existing annotation
                AreaAnnotation updated = new AreaAnnotation
                {
                    // It's important to set existed annotation Id
                    Id = 1,
                    BackgroundColor = 255,
                    Box = new Rectangle(0, 0, 50, 200),
                    CreatedOn = DateTime.Now,
                    Message = "This is updated annotation",
                    Replies = new List<Reply>
                    {
                        new Reply
                        {
                            Comment = "Updated first comment",
                            RepliedOn = DateTime.Now
                        },
                        new Reply
                        {
                            Comment = "Updated second comment",
                            RepliedOn = DateTime.Now
                        }
                    }
                };
                // update annotation
                annotator.Update(updated);
                annotator.Save("result.pdf");
            }
```
{{< /tab >}}
{{< /tabs >}}