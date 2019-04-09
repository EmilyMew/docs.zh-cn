---
title: 如何：在事件发生时向元素应用转换
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
ms.openlocfilehash: 973b9267eaef5d55176633ee80a1dc7f8b043909
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126433"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a>如何：在事件发生时向元素应用转换
此示例演示如何将应用<xref:System.Windows.Media.ScaleTransform>事件的发生时间。 此处说明的概念与用于应用其他类型的转换的概念相同。 有关可用类型的转换的详细信息，请参阅<xref:System.Windows.Media.Transform>类或[转换概述](transforms-overview.md)。  
  
 可以通过以下两种方式之一向元素应用转换：  
  
-   如果这样做*不*希望转换影响布局，请使用<xref:System.Windows.UIElement.RenderTransform%2A>元素的属性。  
  
-   如果您希望转换影响布局，使用<xref:System.Windows.FrameworkElement.LayoutTransform%2A>元素的属性。  
  
 下面的示例应用<xref:System.Windows.Media.ScaleTransform>到<xref:System.Windows.UIElement.RenderTransform%2A>按钮的属性。 当鼠标在按钮上移<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>和<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>的属性<xref:System.Windows.Media.ScaleTransform>设置为`2`，这会导致该按钮会变得更大。 当鼠标离开按钮时，<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>并<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>设置为`1`，这会导致按钮返回到其原始大小。  
  
## <a name="example"></a>示例  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [变换概述](transforms-overview.md)
- [帮助主题](transformations-how-to-topics.md)
- [路由事件概述](../advanced/routed-events-overview.md)
