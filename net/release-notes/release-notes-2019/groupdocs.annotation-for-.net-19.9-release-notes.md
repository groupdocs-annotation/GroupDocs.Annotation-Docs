---
id: groupdocs-annotation-for-net-19-9-release-notes
url: annotation/net/groupdocs-annotation-for-net-19-9-release-notes
title: GroupDocs.Annotation for .NET 19.9 Release Notes
weight: 4
description: ""
keywords: 
productName: GroupDocs.Annotation for .NET
hideChildren: False
---
{{< alert style="info" >}}This page contains release notes for GroupDocs.Annotation for .NET 19.9{{< /alert >}}

## Major Features

{{< alert style="danger" >}}In this version we're introducing new public API which was designed to be simple and easy to use. For more details about new API please check Developer Guide section. The legacy API have been moved into Legacy namespace so after update to this version it is required to make project-wide replacement of namespace usages from GroupDocs.Annotation. to GroupDocs.Annotation.Legacy. to resolve build issues.{{< /alert >}}

## Public API and Backward Incompatible Changes

#### All public types from GroupDocs.Annotation namespace 

1.  Have been moved into **GroupDocs.Annotation.Legacy** namespace
2.  Marked as **Obsolete** with message: *This interface/class/enumeration is obsolete and will be available till January 2020 (v20.1).*

#### Full list of types that have been moved and marked as obsolete:

1.  GroupDocs.Annotation.Cells.CellsCommentator => GroupDocs.Annotation.Legacy.Cells.CellsCommentator
2.  GroupDocs.Annotation.Common.Helper => GroupDocs.Annotation.Legacy.Common.Helper
3.  GroupDocs.Annotation.Common.Logger.ConsoleLogger => GroupDocs.Annotation.Legacy.Common.Logger.ConsoleLogger
4.  GroupDocs.Annotation.Common.Logger.LoggerLevel => GroupDocs.Annotation.Legacy.Common.Logger.LoggerLevel
5.  GroupDocs.Annotation.Core.ConverterToPdf => GroupDocs.Annotation.Legacy.Core.ConverterToPdf
6.  GroupDocs.Annotation.Core.ConverterToWord => GroupDocs.Annotation.Legacy.Core.ConverterToWord
7.  GroupDocs.Annotation.Core.IConverter => GroupDocs.Annotation.Legacy.Core.IConverter
8.  GroupDocs.Annotation.Core.PdfPageRotator => GroupDocs.Annotation.Legacy.Core.PdfPageRotator
9.  GroupDocs.Annotation.Core.PdfToJavaScriptSaver => GroupDocs.Annotation.Legacy.Core.PdfToJavaScriptSaver
10.  GroupDocs.Annotation.Core.PdfToPngSaver => GroupDocs.Annotation.Legacy.Core.PdfToPngSaver
11.  GroupDocs.Annotation.Diagram.DiagramCommentator => GroupDocs.Annotation.Legacy.Diagram.DiagramCommentator
12.  GroupDocs.Annotation.Diagram.DiagramExtractor => GroupDocs.Annotation.Legacy.Diagram.DiagramExtractor
13.  GroupDocs.Annotation.Domain.AnnotationInfo => GroupDocs.Annotation.Legacy.Domain.AnnotationInfo
14.  GroupDocs.Annotation.Domain.AnnotationPermissionInfo => GroupDocs.Annotation.Legacy.Domain.AnnotationPermissionInfo
15.  GroupDocs.Annotation.Domain.AnnotationPermissionRights => GroupDocs.Annotation.Legacy.Domain.AnnotationPermissionRights
16.  GroupDocs.Annotation.Domain.AnnotationReplyInfo => GroupDocs.Annotation.Legacy.Domain.AnnotationReplyInfo
17.  GroupDocs.Annotation.Domain.AnnotationReplyReviewerRights => GroupDocs.Annotation.Legacy.Domain.AnnotationReplyReviewerRights
18.  GroupDocs.Annotation.Domain.AnnotationReviewerRights => GroupDocs.Annotation.Legacy.Domain.AnnotationReviewerRights
19.  GroupDocs.Annotation.Domain.AnnotationSizeInfo => GroupDocs.Annotation.Legacy.Domain.AnnotationSizeInfo
20.  GroupDocs.Annotation.Domain.AnnotationType => GroupDocs.Annotation.Legacy.Domain.AnnotationType
21.  GroupDocs.Annotation.Config.AnnotationConfig => GroupDocs.Annotation.Legacy.Domain.AnnotationAccess
22.  GroupDocs.Annotation.Domain.Containers.DocumentInfoContainer => GroupDocs.Annotation.Legacy.Domain.Containers.DocumentInfoContainer
23.  GroupDocs.Annotation.Domain.Containers.FileContainer => GroupDocs.Annotation.Legacy.Domain.Containers.FileContainer
24.  GroupDocs.Annotation.Domain.Containers.FileTreeContainer => GroupDocs.Annotation.Legacy.Domain.Containers.FileTreeContainer
25.  GroupDocs.Annotation.Domain.ContentControl => GroupDocs.Annotation.Legacy.Domain.ContentControl
26.  GroupDocs.Annotation.Domain.DocumentType => GroupDocs.Annotation.Legacy.Domain.DocumentType
27.  GroupDocs.Annotation.Domain.FileData => GroupDocs.Annotation.Legacy.Domain.DocuFileDatamentType
28.  GroupDocs.Annotation.Domain.FileDescription => GroupDocs.Annotation.Legacy.Domain.FileDescription
29.  GroupDocs.Annotation.Domain.ICommentator => GroupDocs.Annotation.Legacy.Domain.ICommentator
30.  GroupDocs.Annotation.Domain.ILogger => GroupDocs.Annotation.Legacy.Domain.ILogger
31.  GroupDocs.Annotation.Domain.Image.PageImage => GroupDocs.Annotation.Legacy.Domain.Image.PageImage
32.  GroupDocs.Annotation.Domain.Options.ConverterOptions => GroupDocs.Annotation.Legacy.Domain.Options.ConverterOptions
33.  GroupDocs.Annotation.Domain.Options.ExportOptions => GroupDocs.Annotation.Legacy.Domain.Options.ExportOptions
34.  GroupDocs.Annotation.Domain.Options.FileTreeOptions => GroupDocs.Annotation.Legacy.Domain.Options.FileTreeOptions
35.  GroupDocs.Annotation.Domain.Options.ImageOptions => GroupDocs.Annotation.Legacy.Domain.Options.ImageOptions
36.  GroupDocs.Annotation.Domain.Page => GroupDocs.Annotation.Legacy.Domain.Page
37.  GroupDocs.Annotation.Domain.PageCorrector => GroupDocs.Annotation.Legacy.Domain.PageCorrector
38.  GroupDocs.Annotation.Domain.PageData => GroupDocs.Annotation.Legacy.Domain.PageData
39.  GroupDocs.Annotation.Domain.PenStyleEnum => GroupDocs.Annotation.Legacy.Domain.PenStyleEnum
40.  GroupDocs.Annotation.Domain.PageData => GroupDocs.Annotation.Legacy.Domain.PageData
41.  GroupDocs.Annotation.Domain.Point => GroupDocs.Annotation.Legacy.Domain.Point
42.  GroupDocs.Annotation.Domain.Rectangle => GroupDocs.Annotation.Legacy.Domain.Rectangle
43.  GroupDocs.Annotation.Domain.PageData => GroupDocs.Annotation.Legacy.Domain.PageData
44.  GroupDocs.Annotation.Domain.Results.AddReplyResult => GroupDocs.Annotation.Legacy.Domain.Results.AddReplyResult
45.  GroupDocs.Annotation.Domain.Results.CreateAnnotationResult => GroupDocs.Annotation.Legacy.Domain.Results.CreateAnnotationResult
46.  GroupDocs.Annotation.Domain.Results.DeleteAnnotationResult => GroupDocs.Annotation.Legacy.Domain.Results.DeleteAnnotationResult
47.  GroupDocs.Annotation.Domain.Results.DeleteReplyResult => GroupDocs.Annotation.Legacy.Domain.Results.DeleteReplyResult
48.  GroupDocs.Annotation.Domain.Results.EditReplyResult => GroupDocs.Annotation.Legacy.Domain.Results.EditReplyResult
49.  GroupDocs.Annotation.Domain.Results.GetAnnotationPermissionsResult => GroupDocs.Annotation.Legacy.Domain.Results.GetAnnotationPermissionsResult
50.  GroupDocs.Annotation.Domain.Results.GetAnnotationResult => GroupDocs.Annotation.Legacy.Domain.Results.GetAnnotationResult
51.  GroupDocs.Annotation.Domain.Results.GetCollaboratorsResult => GroupDocs.Annotation.Legacy.Domain.Results.GetCollaboratorsResult
52.  GroupDocs.Annotation.Domain.Results.IResult => GroupDocs.Annotation.Legacy.Domain.Results.IResult
53.  GroupDocs.Annotation.Domain.Results.ListAnnotationsResult => GroupDocs.Annotation.Legacy.Domain.Results.ListAnnotationsResult
54.  GroupDocs.Annotation.Domain.Results.ListRepliesResult => GroupDocs.Annotation.Legacy.Domain.Results.ListRepliesResult
55.  GroupDocs.Annotation.Domain.Results.MoveAnnotationResult => GroupDocs.Annotation.Legacy.Domain.Results.MoveAnnotationResult
56.  GroupDocs.Annotation.Domain.Results.ResizeAnnotationResult => GroupDocs.Annotation.Legacy.Domain.Results.ResizeAnnotationResult
57.  GroupDocs.Annotation.Domain.Results.Result => GroupDocs.Annotation.Legacy.Domain.Results.Result
58.  GroupDocs.Annotation.Domain.Results.SaveAnnotationTextResult => GroupDocs.Annotation.Legacy.Domain.Results.SaveAnnotationTextResult
59.  GroupDocs.Annotation.Domain.Results.SetAnnotationPermissionsResult => GroupDocs.Annotation.Legacy.Domain.Results.SetAnnotationPermissionsResult
60.  GroupDocs.Annotation.Domain.Results.SetCollaboratorsResult => GroupDocs.Annotation.Legacy.Domain.Results.SetCollaboratorsResult
61.  GroupDocs.Annotation.Domain.ReviewerInfo => GroupDocs.Annotation.Legacy.Domain.ReviewerInfo
62.  GroupDocs.Annotation.Domain.RowData => GroupDocs.Annotation.Legacy.Domain.RowData
63.  GroupDocs.Annotation.Domain.TextFieldInfo => GroupDocs.Annotation.Legacy.Domain.TextFieldInfo
64.  GroupDocs.Annotation.Domain.StreamUtility => GroupDocs.Annotation.Legacy.Domain.StreamUtility
65.  GroupDocs.Annotation.EmailHtml.CommentRange => GroupDocs.Annotation.Legacy.EmailHtml.CommentRange
66.  GroupDocs.Annotation.EmailHtml.EmailHtmlCommentator => GroupDocs.Annotation.Legacy.EmailHtmlCommentator
67.  GroupDocs.Annotation.EmailHtml.EmailHtmlExtractor => GroupDocs.Annotation.Legacy.EmailHtmlExtractor
68.  GroupDocs.Annotation.Handler.Input.DataObjects.Annotation => GroupDocs.Annotation.Legacy.Handler.Input.DataObjects.Annotation
69.  GroupDocs.Annotation.Handler.Input.DataObjects.AnnotationCollaborator => GroupDocs.Annotation.Legacy.Handler.Input.DataObjects.AnnotationCollaborator
70.  GroupDocs.Annotation.Handler.Input.DataObjects.AnnotationPermission => GroupDocs.Annotation.Legacy.Handler.Input.DataObjects.AnnotationPermission
71.  GroupDocs.Annotation.Handler.Input.DataObjects.AnnotationReply => GroupDocs.Annotation.Legacy.Handler.Input.DataObjects.AnnotationReply
72.  GroupDocs.Annotation.Handler.Input.DataObjects.IEntity => GroupDocs.Annotation.Legacy.Handler.Input.DataObjects.IEntity
73.  GroupDocs.Annotation.Handler.Input.DataObjects.User => GroupDocs.Annotation.Legacy.Handler.Input.DataObjects.User
74.  GroupDocs.Annotation.Handler.Input.IAnnotationCollaboratorDataHandler => GroupDocs.Annotation.Legacy.Handler.Input.IAnnotationCollaboratorDataHandler
75.  GroupDocs.Annotation.Handler.Input.IAnnotationDataHandler => GroupDocs.Annotation.Legacy.Handler.Input.IAnnotationDataHandler
76.  GroupDocs.Annotation.Handler.Input.IAnnotationPermissionsDataHandler => GroupDocs.Annotation.Legacy.Handler.Input.IAnnotationPermissionsDataHandler
77.  GroupDocs.Annotation.Handler.Input.IAnnotationReplyDataHandler => GroupDocs.Annotation.Legacy.Handler.Input.IAnnotationReplyDataHandler
78.  GroupDocs.Annotation.Handler.Input.IDocumentDataHandler => GroupDocs.Annotation.Legacy.Handler.Input.IDocumentDataHandler
79.  GroupDocs.Annotation.Handler.Input.IFileDataStore => GroupDocs.Annotation.Legacy.Handler.Input.IFileDataStore
80.  GroupDocs.Annotation.Handler.Input.IInputDataHandler => GroupDocs.Annotation.Legacy.Handler.Input.IInputDataHandler
81.  GroupDocs.Annotation.Handler.Input.IRepository => GroupDocs.Annotation.Legacy.Handler.Input.IRepository
82.  GroupDocs.Annotation.Handler.Input.IUserDataHandler => GroupDocs.Annotation.Legacy.Handler.Input.IUserDataHandler
83.  GroupDocs.Annotation.Handler.Input.Local.AnnotationCollaboratorRepository => GroupDocs.Annotation.Legacy.Handler.Input.Local.AnnotationCollaboratorRepository
84.  GroupDocs.Annotation.Handler.Input.Local.AnnotationPermissionsRepository => GroupDocs.Annotation.Legacy.Handler.Input.Local.AnnotationPermissionsRepository
85.  GroupDocs.Annotation.Handler.Input.Local.AnnotationReplyRepository => GroupDocs.Annotation.Legacy.Handler.Input.Local.AnnotationReplyRepository
86.  GroupDocs.Annotation.Handler.Input.Local.DocumentRepository => GroupDocs.Annotation.Legacy.Handler.Input.Local.DocumentRepository
87.  GroupDocs.Annotation.Handler.Input.Local.FileDataJsonSerializer => GroupDocs.Annotation.Legacy.Handler.Input.Local.FileDataJsonSerializer
88.  GroupDocs.Annotation.Handler.Input.Local.FileStore => GroupDocs.Annotation.Legacy.Handler.Input.Local.FileStore
89.  GroupDocs.Annotation.Handler.Input.Local.InputDataHandler => GroupDocs.Annotation.Legacy.Handler.Input.Local.InputDataHandler
90.  GroupDocs.Annotation.Handler.Input.Local.RepliesDateComparator => GroupDocs.Annotation.Legacy.Handler.Input.Local.RepliesDateComparator
91.  GroupDocs.Annotation.Handler.Input.Local.UserRepository => GroupDocs.Annotation.Legacy.Handler.Input.Local.UserRepository
92.  GroupDocs.Annotation.Handler.Input.Local.XmlFile => GroupDocs.Annotation.Legacy.Handler.Input.Local.XmlFile
93.  GroupDocs.Annotation.Handler.Input.Local.XmlRepository => GroupDocs.Annotation.Legacy.Handler.Input.Local.XmlRepository
94.  GroupDocs.Annotation.Imaging.BlockWithOffset => GroupDocs.Annotation.Legacy.Imaging.BlockWithOffset
95.  GroupDocs.Annotation.Imaging.ImagesCommentator => GroupDocs.Annotation.Legacy.Imaging.ImagesCommentator
96.  GroupDocs.Annotation.Imaging.ImagesCommentator => GroupDocs.Annotation.Legacy.Imaging.ImagesCommentator
97.  GroupDocs.Annotation.Imaging.ImagesExtractor => GroupDocs.Annotation.Legacy.Imaging.ImagesExtractor
98.  GroupDocs.Annotation.Imaging.RepeatingBlockWithOffset => GroupDocs.Annotation.Legacy.Imaging.RepeatingBlockWithOffset
99.  GroupDocs.Annotation.Pdf.PdfCommentator => GroupDocs.Annotation.Legacy.Pdf.PdfCommentator
100.  GroupDocs.Annotation.Pdf.PdfExtractor => GroupDocs.Annotation.Legacy.Pdf.PdfExtractor
101.  GroupDocs.Annotation.Slides.SlidesCommentator => GroupDocs.Annotation.Legacy.Slides.SlidesCommentator
102.  GroupDocs.Annotation.Slides.SlidesExtractor => GroupDocs.Annotation.Legacy.Slides.SlidesExtractor
103.  GroupDocs.Annotation.Words.AnnotationTextRange => GroupDocs.Annotation.Legacy.Words.AnnotationTextRange
104.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedCell => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedCel
105.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedColumn => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedColumn
106.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedComment => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedComment
107.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedDocument => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedDocument
108.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedEndnote => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedEndnote
109.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedFootnote => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedFootnote
110.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedHeaderFooter => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedHeaderFooter
111.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedNoteSeparator => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedNoteSeparator
112.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedPage => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedPage
113.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedRow => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedRow
114.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedSpan => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedSpan
115.  GroupDocs.Annotation.Words.AsposeRenderedDocument.RenderedTextBox => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.RenderedTextBox
116.  GroupDocs.Annotation.Words.AsposeRenderedDocument.StoryLayoutEntity => GroupDocs.Annotation.Legacy.Words.AsposeRenderedDocument.StoryLayoutEntity
117.  GroupDocs.Annotation.Words.InnerAnnotation => GroupDocs.Annotation.Legacy.Words.InnerAnnotation
118.  GroupDocs.Annotation.Words.InnerAnnotationReply => GroupDocs.Annotation.Legacy.Words.InnerAnnotationReply
119.  GroupDocs.Annotation.Words.LayoutCollection => GroupDocs.Annotation.Legacy.Words.LayoutCollection
120.  GroupDocs.Annotation.Words.LayoutEntity => GroupDocs.Annotation.Legacy.Words.LayoutEntity
121.  GroupDocs.Annotation.Words.RectanglesDescendingComparator => GroupDocs.Annotation.Legacy.Words.RectanglesDescendingComparator
122.  GroupDocs.Annotation.Words.WordsCommentator => GroupDocs.Annotation.Legacy.Words.WordsCommentator
123.  GroupDocs.Annotation.Words.WordsExtractor => GroupDocs.Annotation.Legacy.Words.WordsExtractor
124.  GroupDocs.Annotation.Handler.AnnotationHandler => GroupDocs.Annotation.Legacy.Handler.Handler.AnnotationHandler
125.  GroupDocs.Annotation.Handler.AnnotationImageHandler => GroupDocs.Annotation.Legacy.Handler.Handler.AnnotationImageHandler
