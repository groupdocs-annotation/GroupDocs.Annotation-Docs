---
id: add-replies-to-annotation
url: annotation/net/add-replies-to-annotation
title: Add replies to annotation
weight: 1
description: "The page describes how to add annotation replies when collaborate over document using GroupDocs.Annotation for .NET API."
keywords: add annotation reply, reply to annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
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
[GroupDocs.Annotation](https://products.groupdocs.com/annotation/net) allows you to collaborate over document using annotations and annotation replies. 
  
To update an annotation reply, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the input document path or stream.
2.   Instantiate the [User](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models/user) class.
3.   Instantiate the [Reply](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models/reply) class(es).
4.   Instantiate the annotation object of the appropriate type. Available annotation types are listed [here](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels).
5.   Assign the [User](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models/user) class to `Reply.User` property (by default it is "Guest").
6.   Assign the [Reply](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models/reply) class(es) to the `Replies` collection created at previous steps.
7.   Call the  [Add](https://reference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add) method of the [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) class. Specify the annotation.
8.   Call the [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method. Specify the output document path or stream.

The following code snippet shows how to add replies to annotation:

{{< tabs "example1">}}
{{< tab "C#" >}}
```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
	User user1 = new User
	{
		Id = 1,
		Name = "Tom",
		Email = "somemail@mail.com"
	};
	User user2 = new User
	{
		Id = 2,
		Name = "Jack",
		Email = "somebody@mail.com"
	};
	AreaAnnotation area = new AreaAnnotation
	{
		Box = new Rectangle(100, 100, 100, 100),
		CreatedOn = DateTime.Now,
		Message = "This is an area annotation",
		PageNumber = 0,
		Replies = new List<Reply>
		{
			new Reply
			{
				Id = 1,
				Comment = "First comment",
				RepliedOn = DateTime.Now,
				User = user1
			},
			new Reply
			{
				Id = 2,
				Comment = "Second comment",
				RepliedOn = DateTime.Now,
				User = user2,
			}
		}
	};
annotator.Add(area);
annotator.Save("result.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}