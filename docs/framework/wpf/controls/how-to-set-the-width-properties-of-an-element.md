---
title: 如何：设置元素的宽度属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: a5ed67ba20176398a863a1e9826b1eab71b182f2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096870"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>如何：设置元素的宽度属性
## <a name="example"></a>示例  
 此示例中直观地显示差异中的四个宽度相关属性之间的呈现行为[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  
  
 <xref:System.Windows.FrameworkElement>类公开描述的元素的宽度特征的四个属性。 这四个属性可能会发生冲突，并且当他们这样做，将优先的值确定，如下所示：<xref:System.Windows.FrameworkElement.MinWidth%2A>值将优先于<xref:System.Windows.FrameworkElement.MaxWidth%2A>值，后者又优先于<xref:System.Windows.FrameworkElement.Width%2A>值。 第四个属性， <xref:System.Windows.FrameworkElement.ActualWidth%2A>，是只读的并将报告由与布局过程的交互的实际宽度。  
  
 以下[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]示例绘制<xref:System.Windows.Shapes.Rectangle>元素 (`rect1`) 的子级作为<xref:System.Windows.Controls.Canvas>。 可以更改的宽度属性<xref:System.Windows.Shapes.Rectangle>通过使用一系列<xref:System.Windows.Controls.ListBox>表示的属性值的元素<xref:System.Windows.FrameworkElement.MinWidth%2A>， <xref:System.Windows.FrameworkElement.MaxWidth%2A>，和<xref:System.Windows.FrameworkElement.Width%2A>。 以这种方式，以可视化方式显示每个属性的优先级。  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 下面的代码隐藏示例处理事件的<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>事件引发。 每个自定义方法将来自输入<xref:System.Windows.Controls.ListBox>，将值作为分析<xref:System.Double>，并将值应用于指定的宽度与相关属性。 宽度值也转换为字符串和写入到各种<xref:System.Windows.Controls.TextBlock>元素 （这些元素的定义不在所选的 XAML 所示）。  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 有关完整示例，请参阅[宽度属性比较示例](https://go.microsoft.com/fwlink/?LinkID=160050)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [面板概述](panels-overview.md)
- [设置元素的高度属性](how-to-set-the-height-properties-of-an-element.md)
- [宽度属性比较示例](https://go.microsoft.com/fwlink/?LinkID=160050)
