---
id: extract-annotations-from-document
url: annotation/net/extract-annotations-from-document
title: Extract annotations from document
weight: 4
description: "Learn how to extract annotations from document when collaborate, edit and annotate documents using GroupDocs.Annotation for .NET."
keywords: Extract annotations, annotate document, get document annotations
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
[**GroupDocs.Annotation**](https://products.groupdocs.com/annotation/net) provides an ability to extract annotations from document and serializing to XML format.  
To achieve this you should:

*   Instantiate [Annotator](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [LoadOptions](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation.options/loadoptions) object and set `ImportAnnotation = true`;
*   Define variable with type List<AnnotationBase>;
*   Call [Get](https://apireference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/get) method and return result to variable above;
*   Instantiate XmlSerializer object with type List<AnnotationBase>;
*   Using FileStreamobject, serialize annotations to the file as on example below;

The following code demonstrates how to extract annotation metadata from document:

```csharp
// for using this example input file ("annotated.pdf") must be with annotations
using (Annotator annotator = new Annotator("annotated.pdf"))
{
	List<AnnotationBase> annotations = annotator.Get();
    XmlSerializer formatter = new XmlSerializer(typeof(List<AnnotationBase>));
    using (FileStream fs = new FileStream("annotations.xml", FileMode.Create))
    {
    	fs.SetLength(0);
        formatter.Serialize(fs, annotations);
    }
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
