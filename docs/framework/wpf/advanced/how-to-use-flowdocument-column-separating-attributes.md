---
title: 如何：使用 FlowDocument 列分隔特性
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 27491b21da587fa198061ba52d8daed5d3f28de3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410896"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>如何：使用 FlowDocument 列分隔特性
此示例演示如何使用的列分隔功能<xref:System.Windows.Documents.FlowDocument>。  
  
## <a name="example"></a>示例  
 下面的示例定义<xref:System.Windows.Documents.FlowDocument>，并设置<xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>， <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>，和<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>属性。  <xref:System.Windows.Documents.FlowDocument>包含示例内容了一段。  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 下图显示的效果<xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>， <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>，并<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>特性在所呈现<xref:System.Windows.Documents.FlowDocument>。  
  
 ![显示 FlowDocument Intra 列属性的屏幕截图。](./media/how-to-use-flowdocument-column-separating-attributes/flowdocument-intra-column.png)
