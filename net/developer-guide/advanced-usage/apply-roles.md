---
id: apply-roles
url: annotation/net/apply-roles
title: User roles
weight: 11
description: "Following this guide you will learn how to user role affects GroupDocs.Annotation for .NET API behaviour"
keywords: Role
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using C#
    showVideo: False
    howTo:
        name: How to apply user roles
        description: Learn how to apply user roles with this step by step guide
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass input PDF file path as a constructor parameter.
        - name: Create an instance of any annotation
          text: Create an instance of any annotation class
        - name: Add replies list to the annotation
          text: Initialize Replies property on the annotation object
        - name: Add user with required role to the Replies list
          text: Initialize User property on the Reply object
---

Starting from version 22.11 it is possible to specify a user role for each user.

While working with the replies, you can attach a User object to any Reply. This user object often represents the author of the reply. From now you can also secify a role of the user. If the user role is "Viewer", his replies **will not** be applied to the document. If the user role is "Editor", his replies **will** be applied. This functionality allows you to control whether user can or cannot leave his comments on the document.

This sample shows how you can add a user role: 

```csharp

using (Annotator annotator = new Annotator("input.pdf-file"))
{
  AreaAnnotation area = new AreaAnnotation
  {
    BackgroundColor = 65535,
    Box = new Rectangle(100, 100, 100, 100),
    CreatedOn = DateTime.Now,
    Message = "This is area annotation",
    Opacity = 0.7,
    PageNumber = 0,
    Replies = new List<Reply>
    {
        new Reply 
        {
            Comment = "This comment will be applied",
            RepliedOn = DateTime.Now,
            User = new User(1, "Reviewer", Role.Editor)
        },
        new Reply
        {
            Comment = "This comment will NOT be applied",
            RepliedOn = DateTime.Now,
            User = new User(1, "Member", Role.Viewer)
        }
    }
  };

  annotator.Add(area);
  annotator.Save("result_export");
}
```

## More resources
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
