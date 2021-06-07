---
id: add-replies-to-annotation
url: annotation/net/add-replies-to-annotation
title: Add replies to annotation
weight: 1
description: "Check this guide to learn how to add annotation replies when collaborate over document using GroupDocs.Annotation for .NET API."
keywords: How to add annotation reply, add annotation reply, add reply, reply to annotation
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) provides an ability for several users to collaborate over document via annotations and annotation replies. Adding reply to an annotation via code is as easy as specifying reply content and related user object.  
  
Here are the steps to add annotation replies:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [User](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models/user) object;
*   Instantiate [Reply](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models/reply) object(s);
*   Instantiate annotation object of desired type. Available annotation types are listed [here](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels);
*   Assign [User](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models/user) object to Reply. User property (or by default will be "Guest");
*   Assign [Reply](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.models/reply) object(s) to Replies collection of an annotation object created at previous steps;
*   Call [Add](https://apireference.groupdocs.com/annotation/net/groupdocs.annotation/annotator/methods/add) method of [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object and pass annotation to it;
*   Call [Save](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream;

The following code demonstrates how to add replies to annotation:

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
