---
id: update-annotations
url: annotation/net/update-annotations
title: Update annotations
weight: 6
description: "Check this article and learn how to edit annotation properties - change annotation position, size, appearance etc. when annotate documents using GroupDocs.Annotation for .NET."
keywords: Update annotations, Edit annotation, Change annotation properties
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
Sometimes it's needed to change different annotation properties - move annotation to another position within document, change annotation size, color, text or even select different annotation type. You can easily do this using [**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) by specifying annotation [Id property](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/annotationbase/properties/id) (which is unique for each annotation object within document) and other updated annotation properties. Another way is to update multiple annotations at once - you just need to provide collection of updated annotation objects which will replace all existing document annotations.  

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Create some [AnnotationBase](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/annotationbase) implementation and set Id of existed annotation (if annotation with that Id not found, nothing will be changed) or path list of annotations (all existed annotations will be removed);
*   Call [Update](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/update/index) method of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with passed annotations;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream and [SaveOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/saveoptions) object;

The following code demonstrates how to update annotations:

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

Also annotation could be updated using Id. Note, that for using this case is necessary need to set annotation Id property. It’s need because **GroupDocs.Annotation** must know which annotation must be changed. Or you can pass list of annotations. In that case all previous annotations will be replaced by new list.

*    Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream
*   Create some [AnnotationBase](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/annotationbase) implementation and set Id of existed annotation (if annotation with that Id not found, nothing will be changed) or path list of annotations (all existed annotations will be removed);
*   Call [Update](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/update/index) method of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with passed annotations;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream;

The following code demonstrates how to update annotations using Id:

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

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/net/developer-guide/advanced-usage/_index.md" >}}).

### GitHub Examples
You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Annotation for .NET examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET)
*   [GroupDocs.Annotation for Java examples, plugins, and showcase](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java)
*   [Document Annotation for .NET MVC UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-MVC)
*   [Document Annotation for .NET App WebForms UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-.NET-WebForms)
*   [Document Annotation for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Dropwizard)
*   [Document Annotation for Java Spring UI Example](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java-Spring)
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
