---
id: apply-roles
url: annotation/net/apply-roles
title: User roles
weight: 11
description: "The page describes how to implement user roles in GroupDocs.Annotation for .NET API."
keywords: user, role
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

GroupDocs.Annotation v22.11 and later allows you to specify a user role for each user.

You can specify a [User](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models/user/) object for any reply. This object represents the author of the reply. You can also set a role of the user:
- **Viewer** - GroupDocs.Annotation does not add their replies to the document.
- **Editor** - GroupDocs.Annotation adds their replies. 
Use this feature to control if a user can or cannot add comments to the document.

The following code snippet shows how to add a user role: 

{{< tabs "example1">}}
{{< tab "C#" >}} 
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
{{< /tab >}}
{{< /tabs >}}