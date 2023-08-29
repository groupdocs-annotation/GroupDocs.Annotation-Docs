---
id: add-squiggly-annotation
url: annotation/java/add-squiggly-annotation
title: Add squiggly annotation
weight: 15
description: "The page describes how to add squiggly annotation to a document using GroupDocs.Annotation for Java."
keywords: squiggly annotation, add annotation
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
        description: Learn how to add squiggly annotation to document step by step
        steps:
        - name: Load source file an instance Annotator
          text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
        - name: Annotation class declaration
          text: Create an instance of SquigglyAnnotation class.
        - name: Specify annotation options 
          text: In the SquigglyAnnotation class constructor, pass parameters.
        - name: Add annotation to the document
          text: Call Annotator class .add() method and pass the class name SquigglyAnnotation.
        - name: Save document with annotation
          text: Call Annotator class .save() method and pass output path file.
toc: True
---
Squiggly annotation marks text with a squiggly styling as shown in the picture below:

![](/annotation/net/images/add-squiggly-annotation.png)

You can specify the following properties of the [SquigglyAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/) class:

*   [FontColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/#setFontColor-java.lang.Integer-) defines the color of the annotation text
*   [Opacity](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/#setOpacity-java.lang.Double-) allows you to set the annotation opacity
*   [Points](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/#setPoints-java.util.List-com.groupdocs.annotation.models.Point--) defines the annotation positions as array of points 
*   [BackgroundColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/#setBackgroundColor-java.lang.Integer-) defines the area background color
*   [SquigglyColor](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/#setSquigglyColor-java.lang.Integer-) defines the annotation line color

To add a squiggly annotation, follow these steps:

1.   Instantiate the [Annotator](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/) class. Specify the input document path or stream.
2.   Instantiate the [SquigglyAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/) class. Specify the appropriate properties (position, page number, etc).
3.   Call the [Add](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#add-com.groupdocs.annotation.models.annotationmodels.AnnotationBase-) method. Specify the [SquigglyAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/) class;
4.  Call the [Save](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation/annotator/#save--) method. Specify the output document path or stream.  

The following code snippet shows how to add [SquigglyAnnotation](https://reference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/squigglyannotation/) to the document:

{{< tabs "example1">}}
{{< tab "Java" >}}
```java
//Add squiggly annotation to the document from local disk
try(final Annotator annotator = new Annotator("input.pdf")){
	SquigglyAnnotation squigglyAnnotation = new SquigglyAnnotation();
	squigglyAnnotation.setCreatedOn(new Date());
	squigglyAnnotation.setFontColor(65535);
	squigglyAnnotation.setBackgroundColor(16761035);
	squigglyAnnotation.setMessage("This is squiggly annotation");
	squigglyAnnotation.setOpacity(0.7);
	squigglyAnnotation.setPageNumber(0);
	squigglyAnnotation.setSquigglyColor(1422623);//Supported only Word and PDF
	List points = new ArrayList<Point>();
	points.add(new Point(80, 730));
	points.add(new Point(240, 730));
	points.add(new Point(80, 650));
	points.add(new Point(240, 650));

	Reply reply1 = new Reply();
	reply1.setComment("First comment");
	reply1.setRepliedOn(new Date());

	Reply reply2 = new Reply();
	reply2.setComment("Second comment");
	reply2.setRepliedOn(new Date());

	List<Reply> replies = new ArrayList<>();
	replies.add(reply1);
	replies.add(reply2);

	squigglyAnnotation.setReplies(replies);

	annotator.add(squigglyAnnotation);
	annotator.save("result_squiggly_annotation.pdf");
}
```
{{< /tab >}}
{{< /tabs >}}