---
id: update-annotations
url: annotation/java/update-annotations
title: Update annotations
weight: 6
description: "Check this article and learn how to edit annotation properties - change annotation position, size, appearance etc. when annotate documents using GroupDocs.Annotation for Java."
keywords: Update annotations, Edit annotation, Change annotation properties
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
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
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/java) allows you to update annotations.  

To update annotations, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Create an [AnnotationBase](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/annotationbase) implementation and set Id of existed annotation (if annotation with that Id is not found, it is ignored) or path list of annotations (all existed annotations are removed).
3.   Call the [update](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#update-java.util.List-com.groupdocs.annotation.models.annotationmodels.AnnotationBase--) method of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify annotations.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code demonstrates how to update annotations:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates how to update annotation.

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");
try {
    // Create an instance of Reply class and add comments
    Reply reply1 = new Reply();
    reply1.setComment("Original first comment");
    reply1.setRepliedOn(Calendar.getInstance().getTime());

    Reply reply2 = new Reply();
    reply2.setComment("Original second comment");
    reply2.setRepliedOn(Calendar.getInstance().getTime());

    java.util.List<Reply> replies =  new ArrayList<Reply>();
    replies.add(reply1);
    replies.add(reply2);

    // Create an instance of AreaAnnotation class and set options
    AreaAnnotation original = new AreaAnnotation();
    original.setId(1);
    original.setBackgroundColor(65535);
    original.setBox(new Rectangle(100, 100, 100, 100));
    original.setCreatedOn(Calendar.getInstance().getTime());
    original.setMessage("This is original annotation");
    original.setReplies(replies);
    
    // Add original annotation
    annotator.add(original);
    
    // Save to file
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
LoadOptions tmp0 = new LoadOptions();

// Open annotated document
Annotator annotator1 = new Annotator("outputPath", tmp0);
try {
    // Create an instance of Reply class and add comments
    Reply reply1 = new Reply();
    reply1.setComment("Updated first comment");
    reply1.setRepliedOn(Calendar.getInstance().getTime());

    Reply reply2 = new Reply();
    reply2.setComment("Updated second comment");
    reply2.setRepliedOn(Calendar.getInstance().getTime());

    java.util.List<Reply> replies =  new ArrayList<Reply>();
    replies.add(reply1);
    replies.add(reply2);

    // Suggest we want change some properties of existed annotation
    AreaAnnotation updated = new AreaAnnotation();
    updated.setId(1);
    updated.setBackgroundColor(255);
    updated.setBox(new Rectangle(0, 0, 50, 200));
    updated.setCreatedOn(Calendar.getInstance().getTime());
    updated.setMessage("This is updated annotation");
    updated.setReplies(replies);
    
    // update annotation
    annotator1.update(updated);
    
    // Save to file
    annotator1.save(outputPath);
} finally {
    if (annotator1 != null) {
        annotator1.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}

You can also update annotation using Id or pass the list of annotations. In that case all previous annotations will be replaced by new list.

To do this, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Create an [AnnotationBase](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/annotationbase) implementation and set Id of existed annotation (if annotation with that Id is not found, it is ignored) or path list of annotations (all existed annotations will be removed).
3.   Call the [update()]https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#update-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify annotations.
4.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code demonstrates how to update annotations using Id:

{{< tabs "example2">}}
{{< tab "Java" >}}
```java
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