---
title: 批注概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- highlights [WPF]
- documents [WPF], annotations
- sticky notes [WPF]
ms.assetid: 716bf474-29bd-4c74-84a4-8e0744bdad62
ms.openlocfilehash: faf2e9bbe23acfd46ee98e1f0fca01b7563ede73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122442"
---
# <a name="annotations-overview"></a>批注概述
在纸质文档上编写说明或注释毫不稀奇，我们几乎认为这是理所当然的。 这些说明或注释就是“批注”，我们将其添加到文档，用于标注信息或突出显示兴趣项以供日后参考。 虽然在打印文档上编写注释很简单也很平常，但是就算在所有电子文档上添加个人注释，功能上却通常有很多限制。  
  
 本主题介绍几个常见类型的批注，特别是粘滞便笺和突出显示，并说明了如何将[!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)]简化这些类型的应用程序可以通过 Windows Presentation Foundation (WPF) 文档中的批注查看控件。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 支持批注的文档查看控件包括<xref:System.Windows.Controls.FlowDocumentReader>并<xref:System.Windows.Controls.FlowDocumentScrollViewer>，以及控件派生自<xref:System.Windows.Controls.Primitives.DocumentViewerBase>如<xref:System.Windows.Controls.DocumentViewer>和<xref:System.Windows.Controls.FlowDocumentPageViewer>。  

<a name="caf1_type_stickynotes"></a>   
## <a name="sticky-notes"></a>便笺  
 平常的便笺是将信息写在小块彩纸上，随后将这张彩纸“粘贴”到文档。 数字便笺为电子文档提供类似的功能，但灵活性更高，可包括许多其他类型的内容，如键入文本、手写注释（如 [!INCLUDE[TLA#tla_tpc](../../../../includes/tlasharptla-tpc-md.md)]“墨迹”笔划）或 Web 链接。  
  
 下图显示了突出显示、文本便笺以及墨迹便笺批注的一些示例。  
  
 ![突出显示、文本和墨迹便笺批注。](./media/caf-stickynote.jpg "CAF_StickyNote")  
  
 下面的示例演示了可用于在应用程序中启用批注支持的方法。  
  
 [!code-csharp[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXml/CSharp/Window1.xaml.cs#docviewxmlstartannotations)]
 [!code-vb[DocViewerAnnotationsXml#DocViewXmlStartAnnotations](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DocViewerAnnotationsXml/visualbasic/window1.xaml.vb#docviewxmlstartannotations)]  
  
<a name="caf1_type_callouts"></a>   
## <a name="highlights"></a>突出显示  
 当人们在纸质文档上作标记时，往往使用创造性的方法来突出显示兴趣项，例如对于句子中的某些字词，加下划线、高亮显示、圈出，或者将在空白的地方绘制标记或符号。  [!INCLUDE[TLA#tla_caf](../../../../includes/tlasharptla-caf-md.md)] 中的突出显示批注具有类似的功能，用于标记在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 文档查看控件中显示的信息。  
  
 下图演示了一个突出显示批注的示例。  
  
 ![突出显示批注](./media/caf-callouts.png "CAF_Callouts")  
  
 用户通常通过首先选择一些文本或自己感兴趣的项，然后右键单击以显示创建批注<xref:System.Windows.Controls.ContextMenu>批注选项。  下面的示例演示[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]可用于声明<xref:System.Windows.Controls.ContextMenu>用户可以访问创建和管理批注的路由命令。  
  
 [!code-xaml[DocViewerAnnotationsXps#CreateDeleteAnnotations](~/samples/snippets/csharp/VS_Snippets_Wpf/DocViewerAnnotationsXps/CSharp/Window1.xaml#createdeleteannotations)]  
  
<a name="caf1_framework_data_anchoring"></a>   
## <a name="data-anchoring"></a>数据锚定  
 [!INCLUDE[TLA2#tla_caf](../../../../includes/tla2sharptla-caf-md.md)] 将批注与用户选择的数据绑定，而不仅仅是绑定到显示视图中的某个位置。 因此，如果文档视图更改（例如，当用户滚动显示窗口或者调整其大小时），批注将仍然跟随它绑定到的所选数据。 例如，下图显示了用户在所选文本上做的批注。 当文档视图更改时（滚动、调整大小、缩放或者移动），突出显示批注将与最初所选数据一起移动。  
  
 ![批注数据锚定](./media/caf-dataanchoring.png "CAF_DataAnchoring")  
  
<a name="matching_annotations_with_annotated_objects"></a>   
## <a name="matching-annotations-with-annotated-objects"></a>匹配批注与批注对象  
 你可以将批注与对应的批注对象匹配。 以具有注释窗格的简单文档读取器应用程序为例。 注释窗格可能是一个列表框，用于显示锚定到文档的批注列表的文本。 如果用户在列表框中选择一项，应用程序将显示相应的批注对象所锚定到的文档段落。  
  
 下面的示例演示如何实现充当注释窗格的此类列表框的事件处理程序。  
  
 [!code-csharp[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/CSharp/Window1.xaml.cs#handler)]
 [!code-vb[FlowDocumentAnnotatedViewer#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentAnnotatedViewer/visualbasic/window1.xaml.vb#handler)]  
  
 另一个示例方案涉及到应用程序，使交换批注和文档通过电子邮件的读取者之间的粘滞便笺。 凭借此功能，这些应用程序可以将读取器导航到包含要交换的批注的页面。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Primitives.DocumentViewerBase>
- <xref:System.Windows.Controls.DocumentViewer>
- <xref:System.Windows.Controls.FlowDocumentPageViewer>
- <xref:System.Windows.Controls.FlowDocumentScrollViewer>
- <xref:System.Windows.Controls.FlowDocumentReader>
- <xref:System.Windows.Annotations.IAnchorInfo>
- [批注架构](annotations-schema.md)
- [ContextMenu 概述](../controls/contextmenu-overview.md)
- [命令概述](commanding-overview.md)
- [流文档概述](flow-document-overview.md)
- [如何：将命令添加到菜单项](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
