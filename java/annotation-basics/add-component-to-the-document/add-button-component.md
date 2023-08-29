---
id: add-button-component
url: annotation/java/add-button-component
title: Add button component
weight: 1
description: "The page describes how to add button component to a document using GroupDocs.Annotation for Java."
keywords: button component, add
productName: GroupDocs.Annotation for Java
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: Represents text or graphic notes, comments and remarks attached to a specific part of the content of the document using Java
    showVideo: False
    howTo:
        name: How to annotate a document
        description: Learn how to add button component to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of ButtonComponent class.
        - name: Specify annotation options 
          text: In the ButtonComponent class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name ButtonComponent.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Button component creates a button component as shown in the picture below: 

![](/annotation/net/images/add-button-component.png)

You can specify the following properties of the [ButtonComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/) class:

*   [Box](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position
*   [PenColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/#setPenColor-java.lang.Integer-) defines the frame color

To add a button component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/) class. Specify the input document path or stream.
2.   Instantiate the [ButtonComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [ButtonComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/) class.
4.   Call the [Save](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows how to add [ButtonComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/buttoncomponent/) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
try(final Annotator annotator = new Annotator(Constants.INPUT_PDF)) {
	ButtonComponent buttonComponent = new ButtonComponent();
	buttonComponent.setCreatedOn(new Date());
	buttonComponent.setStyle(BorderStyle.DASHED);
	buttonComponent.setMessage("This is button component");
	buttonComponent.setBorderColor(1422623);
	buttonComponent.setPenColor(14527697);
	buttonComponent.setButtonColor(10832612);
	buttonComponent.setPageNumber(0);
	buttonComponent.setBorderWidth(12);
	buttonComponent.setBox(new Rectangle(100, 300, 90, 30));

	Reply reply1 = new Reply();
	reply1.setComment("First comment");
	reply1.setRepliedOn(new Date());

	Reply reply2 = new Reply();
	reply2.setComment("Second comment");
	reply2.setRepliedOn(new Date());

	List<Reply> replies = new ArrayList<>();
	replies.add(reply1);
	replies.add(reply2);

	buttonComponent.setReplies(replies);

	annotator.add(buttonComponent);
	annotator.save("result_button_component.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}