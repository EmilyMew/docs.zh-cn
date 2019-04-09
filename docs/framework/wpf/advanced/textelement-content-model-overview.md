---
title: TextElement 内容模型概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: ecb9441bc63eae41cfbbadf3bf81b0e5392bd0cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125115"
---
# <a name="textelement-content-model-overview"></a>TextElement 内容模型概述
此内容模型概述介绍了支持的内容<xref:System.Windows.Documents.TextElement>。 <xref:System.Windows.Documents.Paragraph>类是一种<xref:System.Windows.Documents.TextElement>。 内容模型描述哪些对象/元素可包含在其他对象/元素中。 本概述概括了用于从派生的对象的内容模型<xref:System.Windows.Documents.TextElement>。 有关详细信息，请参阅[流文档概述](flow-document-overview.md)。  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>内容模型图  
 下图概括了内容模型，用于类派生自<xref:System.Windows.Documents.TextElement>以及其他非`TextElement`适应此模型的类。  
  
 ![关系图：流内容包含架构](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 如上面的关系图所示，元素的子级不一定由类是否派生自<xref:System.Windows.Documents.Block>类或<xref:System.Windows.Documents.Inline>类。 例如， <xref:System.Windows.Documents.Span> (<xref:System.Windows.Documents.Inline>的派生类) 只能有<xref:System.Windows.Documents.Inline>子元素，但<xref:System.Windows.Documents.Figure>(还<xref:System.Windows.Documents.Inline>的派生类) 只能有<xref:System.Windows.Documents.Block>子元素。 因此，关系图可用于快速确定哪些元素可以包含在其他元素中。 例如，让我们使用关系图来确定如何构造流内容的<xref:System.Windows.Controls.RichTextBox>。  
  
1.  一个<xref:System.Windows.Controls.RichTextBox>必须包含<xref:System.Windows.Documents.FlowDocument>又必须包含<xref:System.Windows.Documents.Block>-派生的对象。 以下是上述关系图中的相应部分。  
  
     ![关系图：RichTextBox 包含规则](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     到此为止，标记可能类似于所示内容。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2.  根据关系图中，有几个<xref:System.Windows.Documents.Block>元素可供选择包括<xref:System.Windows.Documents.Paragraph>， <xref:System.Windows.Documents.Section>， <xref:System.Windows.Documents.Table>， <xref:System.Windows.Documents.List>，并<xref:System.Windows.Documents.BlockUIContainer>（请参阅上图中的 Block 派生类）。 假设我们想<xref:System.Windows.Documents.Table>。 上图中，根据<xref:System.Windows.Documents.Table>包含<xref:System.Windows.Documents.TableRowGroup>包含<xref:System.Windows.Documents.TableRow>元素，其中包含<xref:System.Windows.Documents.TableCell>元素包含<xref:System.Windows.Documents.Block>-派生的对象。 以下是有关的对应部分<xref:System.Windows.Documents.Table>取自上述关系图。  
  
     ![关系图：父&#47;表的子架构](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     下面是相应的标记。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3.  同样，一个或多个<xref:System.Windows.Documents.Block>下需要元素<xref:System.Windows.Documents.TableCell>。 为简单起见，在单元格内部放置一些文本。 我们可以使用执行此类情况的操作<xref:System.Windows.Documents.Paragraph>与<xref:System.Windows.Documents.Run>元素。 下面是显示的关系图中的对应部分<xref:System.Windows.Documents.Paragraph>花费<xref:System.Windows.Documents.Inline>元素，而<xref:System.Windows.Documents.Run>(<xref:System.Windows.Documents.Inline>元素) 只能采用纯文本。  
  
     ![关系图：父&#47;paragraph](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![关系图：父&#47;run](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 下面是标记中的完整示例。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>以编程方式处理 TextElement 内容  
 内容<xref:System.Windows.Documents.TextElement>组成的集合，因此以编程方式操作的内容<xref:System.Windows.Documents.TextElement>对象通过使用这些集合。 有三个不同的集合使用<xref:System.Windows.Documents.TextElement>-派生的类：  
  
-   <xref:System.Windows.Documents.InlineCollection>:表示 <xref:System.Windows.Documents.Inline> 元素的集合。 <xref:System.Windows.Documents.InlineCollection> 定义允许的子内容的<xref:System.Windows.Documents.Paragraph>， <xref:System.Windows.Documents.Span>，和<xref:System.Windows.Controls.TextBlock>元素。  
  
-   <xref:System.Windows.Documents.BlockCollection>:表示 <xref:System.Windows.Documents.Block> 元素的集合。 <xref:System.Windows.Documents.BlockCollection> 定义允许的子内容的<xref:System.Windows.Documents.FlowDocument>， <xref:System.Windows.Documents.Section>， <xref:System.Windows.Documents.ListItem>， <xref:System.Windows.Documents.TableCell>， <xref:System.Windows.Documents.Floater>，并<xref:System.Windows.Documents.Figure>元素。  
  
-   <xref:System.Windows.Documents.ListItemCollection>:流内容元素，表示特定内容项中有序或无序<xref:System.Windows.Documents.List>。  
  
 您可以操作 （添加或删除项目） 从这些集合使用的相应属性**Inlines**，**块**，和**ListItems**。 以下示例演示如何操作 s p a n 使用的内容**Inlines**属性。  
  
> [!NOTE]
>  表格使用多个集合来操作其内容，但这里不对其进行说明。 有关详细信息，请参阅[表概述](table-overview.md)。  
  
 下面的示例创建一个新<xref:System.Windows.Documents.Span>对象，然后使用`Add`方法添加两个文本运行的子内容作为<xref:System.Windows.Documents.Span>。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 下面的示例创建一个新<xref:System.Windows.Documents.Run>元素，并将它插入的开始处<xref:System.Windows.Documents.Span>。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 以下示例删除上次<xref:System.Windows.Documents.Inline>中的元素<xref:System.Windows.Documents.Span>。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 以下示例清除所有内容 (<xref:System.Windows.Documents.Inline>元素) 从<xref:System.Windows.Documents.Span>。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>共享此内容模型的类型  
 以下类型均继承自<xref:System.Windows.Documents.TextElement>类，并可用于显示本概述中所述的内容。  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 请注意，此列表仅包含一起分发的非抽象类型[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]。 你可能会使用继承自其他类型<xref:System.Windows.Documents.TextElement>。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>可包含 TextElement 对象的类型  
 请参阅[WPF 内容模型](../controls/wpf-content-model.md)。  
  
## <a name="see-also"></a>请参阅

- [通过 Blocks 属性操作 FlowDocument](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [通过 Blocks 属性操作流内容元素](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [通过 Blocks 属性操作 FlowDocument](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [通过 Columns 属性操作表的列](how-to-manipulate-table-columns-through-the-columns-property.md)
- [通过 RowGroups 属性操作表的行组](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
