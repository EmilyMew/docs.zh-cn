---
title: 如何：获取视觉对象的偏移量
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: 4787b771c7e59a8b033b9267079c068a5845a1e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093405"
---
# <a name="how-to-get-the-offset-of-a-visual"></a>如何：获取视觉对象的偏移量
这些示例显示如何检索相对于其父级或任何祖先或后代的可视对象的偏移量的值。  
  
## <a name="example"></a>示例  
 以下标记示例演示<xref:System.Windows.Controls.TextBlock>定义与<xref:System.Windows.FrameworkElement.Margin%2A>值为 4。  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 下面的代码示例演示如何使用<xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A>方法来检索其中的偏移量<xref:System.Windows.Controls.TextBlock>。 偏移量的值包含在返回<xref:System.Windows.Vector>值。  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 偏移量将考虑<xref:System.Windows.FrameworkElement.Margin%2A>值。 在这种情况下，<xref:System.Windows.Vector.X%2A>为 4，和<xref:System.Windows.Vector.Y%2A>为 4。  
  
 返回的偏移量的值是相对于父级的<xref:System.Windows.Media.Visual>。 如果你想要返回的不是相对于父级的偏移量的值<xref:System.Windows.Media.Visual>，使用<xref:System.Windows.Media.Visual.TransformToAncestor%2A>方法。  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a>获取偏移量相对于上级  
 以下标记示例演示<xref:System.Windows.Controls.TextBlock>嵌套在两个<xref:System.Windows.Controls.StackPanel>对象。  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 下图显示标记的结果。  
  
 ![对象的偏移量值](./media/visualoffset-01.png "VisualOffset_01")  
嵌套在两个面板的 TextBlock  
  
 下面的代码示例演示如何使用<xref:System.Windows.Media.Visual.TransformToAncestor%2A>方法来检索其中的偏移量<xref:System.Windows.Controls.TextBlock>相对于包含<xref:System.Windows.Window>。 偏移量的值包含在返回<xref:System.Windows.Media.GeneralTransform>值。  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 偏移量会考虑<xref:System.Windows.FrameworkElement.Margin%2A>值中包含的所有对象<xref:System.Windows.Window>。 在这种情况下，<xref:System.Windows.Vector.X%2A>为 28 (16 + 8 + 4) 和<xref:System.Windows.Vector.Y%2A>为 28。  
  
 返回的偏移量的值是相对于相对的祖先<xref:System.Windows.Media.Visual>。 如果你想要返回的偏移量的值是相对于的后代<xref:System.Windows.Media.Visual>，使用<xref:System.Windows.Media.Visual.TransformToDescendant%2A>方法。  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a>获取偏移量相对于后代  
 以下标记示例演示<xref:System.Windows.Controls.TextBlock>包含在<xref:System.Windows.Controls.StackPanel>对象。  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 下面的代码示例演示如何使用<xref:System.Windows.Media.Visual.TransformToDescendant%2A>方法来检索其中的偏移量<xref:System.Windows.Controls.StackPanel>相对于其子<xref:System.Windows.Controls.TextBlock>。 偏移量的值包含在返回<xref:System.Windows.Media.GeneralTransform>值。  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 偏移量将考虑<xref:System.Windows.FrameworkElement.Margin%2A>的所有对象的值。 在这种情况下，<xref:System.Windows.Vector.X%2A>为-4，和<xref:System.Windows.Vector.Y%2A>-4。 偏移量的值是负值，因为父对象产生负面偏移量相对于其子对象。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [WPF 图形呈现疑难解答](wpf-graphics-rendering-overview.md)
