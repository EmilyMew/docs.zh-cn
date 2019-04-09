---
title: 如何：以编程方式更改 TextWrapping 属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], changing TextWrapping property programmatically
- TextWrapping property [WPF], changing programmatically
ms.assetid: 30d25554-4c82-4df9-a8d6-35683a4a13bb
ms.openlocfilehash: 21ca31d24121492fe6927cd533d5b3c0785b5a28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095836"
---
# <a name="how-to-change-the-textwrapping-property-programmatically"></a>如何：以编程方式更改 TextWrapping 属性
## <a name="example"></a>示例  
 下面的代码示例演示如何更改的值<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>属性以编程方式。  
  
 三个<xref:System.Windows.Controls.Button>元素中放置<xref:System.Windows.Controls.StackPanel>中的元素[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 每个<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件<xref:System.Windows.Controls.Button>对应于代码中的事件处理程序。 事件处理程序使用相同的名称<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>值，它们将应用于`txt2`时单击该按钮。 此外中的文本`txt1`(<xref:System.Windows.Controls.TextBlock>不会显示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]) 将更新以反映属性中的更改。  
  
 [!code-xaml[TextWrapProperty#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml#1)]  
  
 [!code-csharp[TextWrapProperty#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextWrapProperty/CSharp/Window1.xaml.cs#2)]
 [!code-vb[TextWrapProperty#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextWrapProperty/VisualBasic/Pane1.xaml.vb#2)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>
- <xref:System.Windows.TextWrapping>
