---
id: add-checkbox-component
url: annotation/java/add-checkbox-component
title: Add checkbox component
weight: 1
description: "The page describes how to add checkbox component to a document using GroupDocs.Annotation for Java."
keywords: checkbox component, add component
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
        description: Learn how to add check box component to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of CheckBoxComponent class.
        - name: Specify annotation options 
          text: In the CheckBoxComponent class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name CheckBoxComponent.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Checkbox component creates a checkbox as shown in the picture below: 

![](/annotation/net/images/add-checkbox-component.png)

You can specify the following properties of the [CheckBoxComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/) class:

*   [Box](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position
*   [PenColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/#setPenColor-java.lang.Integer-) defines the frame color

To add a checkbox component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/) class. Specify the input document path or stream.
2.   Instantiate the [CheckboxComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [CheckboxComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/) class.
4.   Call the [Save](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows how to add [CheckboxComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/checkboxcomponent/) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
try(final Annotator annotator = new Annotator(Constants.INPUT_PDF)) {
	CheckBoxComponent checkbox = new CheckBoxComponent();
	checkbox.setChecked(true);
	checkbox.setBox(new Rectangle(100, 100, 100, 100));
	checkbox.setPenColor(65535);
	checkbox.setStyle(BoxStyle.STAR);
	Reply reply1 = new Reply();
	reply1.setComment("First comment");
	reply1.setRepliedOn(new Date());

	Reply reply2 = new Reply();
	reply2.setComment("Second comment");
	reply2.setRepliedOn(new Date());

	List<Reply> replies = new ArrayList<>();
	replies.add(reply1);
	replies.add(reply2);

	checkbox.setReplies(replies);

	annotator.add(checkbox);
	annotator.save("result_checkbox_component.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}