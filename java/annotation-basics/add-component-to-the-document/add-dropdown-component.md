---
id: add-dropdown-component
url: annotation/java/add-dropdown-component
title: Add dropdown component
weight: 1
description: "The page describes how to add dropdown component to a document using GroupDocs.Annotation for Java."
keywords: dropdown component, add component
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
        description: Learn how to add drop down component to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of DropdownComponent class.
        - name: Specify annotation options 
          text: In the DropdownComponent class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .Add() method and pass the class name DropdownComponent.
        - name: Save document with annotation
          text: Call Annotator class .Save() method and pass output path file.
toc: True
---
Dropdown component creates a combo box as shown in the picture below: 

![](/annotation/net/images/add-dropdown-component.png)

You can specify the following properties of the [DropdownComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/) class:

*   [Box](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/#setBox-com.groupdocs.annotation.models.Rectangle-) defines the annotation position
*   [PenColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/#setPenColor-java.lang.Integer-) defines the frame color
*   [PenStyle](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/#setPenStyle-java.lang.Byte-) defines the frame line style (solid, dash, dot etc.)
*   [PenWidth](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/#setPenWidth-java.lang.Byte-) defines the frame line width in pixels.

To add a dropdown component, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/) class. Specify the input document path or stream.
2.   Instantiate the [DropdownComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [DropdownComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/) class.
4.   Call the [Save](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.

The following code snippet shows how to add [DropdownComponent](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.formatspecificcomponents.pdf/dropdowncomponent/) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
try(final Annotator annotator = new Annotator(Constants.INPUT_PDF)) {
	DropdownComponent dropdownComponent = new DropdownComponent();
	dropdownComponent.setOptions(new ArrayList<>(Arrays.asList("Item1", "Item2", "Item3")));
	dropdownComponent.setSelectedOption(null);
	dropdownComponent.setPlaceholder("Choose option");
	dropdownComponent.setBox(new Rectangle(100, 100, 100, 100));
	dropdownComponent.setCreatedOn(new Date());
	dropdownComponent.setMessage("This is dropdown component");
	dropdownComponent.setPageNumber(0);
	dropdownComponent.setPenColor(65535);
	dropdownComponent.setPenStyle(PenStyle.DOT);
	dropdownComponent.setPenWidth((byte) 3);

	List<Reply> replies = new ArrayList<>();
	Reply reply1 = new Reply();
	reply1.setComment("First comment");
	reply1.setRepliedOn(new Date());

	Reply reply2 = new Reply();
	reply2.setComment("Second comment");
	reply2.setRepliedOn(new Date());

	replies.add(reply1);
	replies.add(reply2);

	dropdownComponent.setReplies(replies);
	annotator.add(dropdownComponent);
	annotator.save("result_dropdown_component.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}