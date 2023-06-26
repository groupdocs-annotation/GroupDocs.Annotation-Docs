---
id: add-replies-to-annotation
url: annotation/java/add-replies-to-annotation
title: Add replies to annotation
weight: 1
description: "The page describes how to add annotation replies when collaborate over document using GroupDocs.Annotation for Java API."
keywords: add annotation reply, reply to annotation
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
    showVideo: False
    howTo:
        name: How to add replies to annotation
        description: Learn how to add replies annotation step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of ButtonComponent class.
        - name: Specify annotation options 
          text: In the ButtonComponent class, pass parameter Reply class with property.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ButtonComponent.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/java) provides an ability to collaborate over document using annotations and annotation replies. 
  
To update an annotation reply, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the input document path or stream.
2.   Instantiate the [User](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/user/) class.
3.   Instantiate the [Reply](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/reply/) class(es).
4.   Instantiate the annotation object of the appropriate type. Available annotation types are listed [here](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/).
5.   Assign the [User](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/user/) class to `Reply.User` property (by default it is "Guest").
6.   Assign the [Reply](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/reply/) class(es) to the `Replies` collection created at previous steps.
7.   Call the  [add()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method of the [Annotator](https://reference.groupdocs.com/java/annotation/com.groupdocs.annotation/Annotator) class. Specify the annotation.
8.   Call the [save()](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows how to add replies to annotation:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
// This example demonstrates adding replies to annotation.

// Create an instance of Annotator class
Annotator annotator = new Annotator("inputPath");
try {
    // Create an instance of User class and add data
    User user1 = new User();
    user1.setId(1);
    user1.setName("Tom");
    user1.setEmail("somemail@mail.com");
    User user2 = new User();
    user2.setId(2);
    user2.setName("Jack");
    user2.setEmail("somebody@mail.com");
    User user3 = new User();
    user3.setId(3);
    user3.setName("Mike");
    user3.setEmail("somemike@mail.com");
    
    // Create an instance of AreaAnnotation class and set options
    AreaAnnotation area = new AreaAnnotation();
    area.setBackgroundColor(65535);
    area.setBox(new Rectangle(100, 100, 100, 100));
    area.setCreatedOn(Calendar.getInstance().getTime());
    area.setMessage("This is area annotation");
    area.setOpacity(0.7);
    area.setPageNumber(0);
    area.setPenColor(65535);
    area.setPenStyle(PenStyle.Dot);
    area.setPenWidth((byte) 3);

    // Create an instance of Reply class and add comments
    Reply reply1 = new Reply();
    reply1.setId(1);
    reply1.setComment("First comment");
    reply1.setRepliedOn(Calendar.getInstance().getTime());
    reply1.setUser(user1);

    Reply reply2 = new Reply();
    reply2.setId(2);
    reply2.setComment("Second comment");
    reply2.setRepliedOn(Calendar.getInstance().getTime());
    reply2.setUser(user2);

    Reply reply3 = new Reply();
    reply3.setId(3);
    reply3.setComment("Third comment");
    reply3.setRepliedOn(Calendar.getInstance().getTime());
    reply3.setUser(user1);

    Reply reply4 = new Reply();
    reply4.setId(4);
    reply4.setComment("Fourth comment");
    reply4.setRepliedOn(Calendar.getInstance().getTime());
    reply4.setUser(user2);
    
    Reply reply5 = new Reply();
    reply5.setId(5);
    reply5.setComment("Five comment");
    reply5.setRepliedOn(Calendar.getInstance().getTime());
    reply5.setUser(user3);

    java.util.List<Reply> replies =  new ArrayList<Reply>();
    replies.add(reply1);
    replies.add(reply2);
    replies.add(reply3);
    replies.add(reply4);
    replies.add(reply5);

    area.setReplies(replies);
    
    // Add annotation and save to file
    annotator.add(area);
    annotator.save("outputPath");
} finally {
    if (annotator != null) {
        annotator.dispose();
    }
}
```
{{< /tab >}}
{{< /tabs >}}