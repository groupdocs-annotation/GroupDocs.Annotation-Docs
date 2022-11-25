---
id: how-to-add-watermark-to-documents
url: annotation/net/how-to-add-watermark-to-documents
title: How to add watermarks to photo or documents in .NET
weight: 6
description: "Programmatically add watermarks to any document, including photos, PDF, word, excell sheets and others using .NET API."
keywords: watermark, watermark photos, add watermark, save watermark, documents watermark
productName: GroupDocs.Annotation for .NET
hideChildren: False
structuredData:
    showOrganization: True
    application:    
        name: GroupDocs Annotation
        description: An examples of how to add watermark to the document using .NET API.
    showVideo: False
    howTo:
        name: How to add watermark annotation
        description: Learn how to programmatically add watermark annotation to the any document
        steps:
          - name: Load source file an instance Annotator
            text: Create an instance of Annotator class and pass source file path as a constructor parameter. You may specify absolute or relative file path as per your requirements. 
          - name: Create watermark object
            text: Create an instance of WatermarkAnnotation class.
          - name: Specify watermark options 
            text: Pass parameters to the WatermarkAnnotation constructor.
          - name: Add watermark annotation to the document
            text: Call method Add() on Annotator object and pass WatermarkAnnotation instance there.
          - name: Save document with annotation
            text: Call method Save() on Annotator object and pass output file destination there.
toc: True
---

## What we offer in context of watermarks

Although GroupDocs.Annotation does not specialise specifically in watermarks, we still provide this opportunity to our users. You can add a text watermark to any of the documents we [support](https://docs.groupdocs.com/annotation/net/supported-document-formats/). You can specify text, choose any font, any colour and size of text, set transparency, angle of text, as well as specify some other useful parameters. You can read more about them [here](https://docs.groupdocs.com/annotation/net/add-watermark-annotation/). At the moment, annotation only allows you to create text annotations, but it allows you to do so programmatically, so even offline. We understand that watermarking is a very complex and important task and it is unlikely to be limited to text-only versions. If this is the case, we recommend that you visit our web application dedicated [specifically to watermarking](https://products.groupdocs.com/watermark/net/).


## Check document preview with a watermark on it

### Check live preview

Of course, when applying any annotation, especially if it is a watermark, you would probably like to see how it looks on the document. For this purpose we have a [web application](https://products.groupdocs.app/annotation/total) which we highly recommend to use. It is absolutely free. You can annotate and move the annotation around on the document. It gives the full feeling of working directly inside the document. 

### Generate preview

You can also check out our article on [how to generate previews programmatically](https://docs.groupdocs.com/annotation/net/how-to-get-document-information-and-generate-preview/) via our .NET API. It will guide you how to apply an annotation and immediately generate a preview of your document with it. This can be useful if you're not sure where and how to put a watermark. In that case you can apply the watermark in different places and generate multiple previews. The generated previews can then be sent to someone for approval. 

## How to add watermark to any document

**Watermark** annotation adds text watermark like shown at the picture below. 

![](/annotation/net/images/add-watermark-annotation.png)

There is an ability to specify the next properties for [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) type:

*   [Box](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/box) - defines annotation position at document page;
*   [Text](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/text) - text of watermark;
*   [FontColor](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontcolor) - color of annotation text;
*   [FontFamily](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontfamily) - font of annotation text;
*   [FontSize](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/fontsize) - size of text font;
*   [Opacity](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/opacity) - allows to set annotation opacity;
*   [Angle](https://reference.groupdocs.com/annotation/net/groupdocs.annotation.models.annotationmodels/watermarkannotation/properties/angle) - watermark text angle;
*   [VerticalAlignment]() - defines vertical alignment on document;
*   [HorizontalAlignment]() - defines horizontal alignment on document.
*   [AutoScale]() - size watermark depends on the word length and document size.

Follow these steps to add Watermark annotation to document:

*   Instantiate [Annotator](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator) object with input document path or stream;
*   Instantiate [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) object with desired properties (position, color, etc);
*   Call [Add](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/add) method and pass [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) object;
*   Call [Save](https://reference.groupdocs.com/net/annotation/groupdocs.annotation/annotator/methods/save/index) method with resultant document path or stream.


The following code demonstrates how to add [WatermarkAnnotation](https://reference.groupdocs.com/net/annotation/groupdocs.annotation.models.annotationmodels/watermarkannotation) to the document:

```csharp
//Add watermark annotation to the document from local disk
using (Annotator annotator = new Annotator("input.pdf"))
{
	WatermarkAnnotation watermark = new WatermarkAnnotation
    {
    	Angle = 75,
        Box = new Rectangle(200, 200, 100, 50),
        CreatedOn = DateTime.Now,
        Text = "Watermark",
        FontColor = 65535,
        FontSize = 12,
        Message = "This is watermark annotation",
        Opacity = 0.7,
        AutoScale = true,
        HorizontalAlignment = HorizontalAlignment.Center,
        VerticalAlignment = VerticalAlignment.Center,
        Replies = new List<Reply>
        {
        	new Reply
            {
            	Comment = "First comment",
                RepliedOn = DateTime.Now
            },
            new Reply
            {
            	Comment = "Second comment",
                RepliedOn = DateTime.Now
            }
        }
    };
    annotator.Add(watermark);
    annotator.Save("result.pdf");
} 

```


## Conclusion

In short, we have learned how to work with watermark using GroupDocs.Annotation .NET API. We have described two options of how you can preview watermark on the document. Moreover, we have offered another resource that extends out functionality - [GroupDocs.Watermark](https://products.groupdocs.com/watermark/net/). Now, you should have enoughh knowledge to start manipulating with watermark using our GroupDocs .NET API. 

## More resources
### Advanced Usage Topics
To learn more about document annotating features, please refer to the [advanced usage section]({{< ref "annotation/net/developer-guide/advanced-usage/_index.md" >}}).
    

### Free Online App
Along with full-featured .NET library we provide simple but powerful free Apps.
You are welcome to annotate your PDF, DOC or DOCX, XLS or XLSX, PPT or PPTX, PNG and other documents with free to use online **[GroupDocs Annotation App](https://products.groupdocs.app/annotation)**.
