---
title: 如何：对 SolidColorBrush 的颜色或不透明度进行动画处理
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: e440cf49b8b16051361650f9659dc6006c2e7b56
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072154"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>如何：对 SolidColorBrush 的颜色或不透明度进行动画处理
此示例演示如何进行动画处理<xref:System.Windows.Media.SolidColorBrush.Color%2A>并<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。  
  
## <a name="example"></a>示例  
 下面的示例使用三个动画进行动画处理<xref:System.Windows.Media.SolidColorBrush.Color%2A>并<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。  
  
-   第一个动画<xref:System.Windows.Media.Animation.ColorAnimation>，会将画笔的颜色改<xref:System.Windows.Media.Colors.Gray%2A>当鼠标进入矩形。  
  
-   下一步的动画，另一个<xref:System.Windows.Media.Animation.ColorAnimation>，会将画笔的颜色改<xref:System.Windows.Media.Colors.Orange%2A>当鼠标离开矩形。  
  
-   最后一个动画， <xref:System.Windows.Media.Animation.DoubleAnimation>，当按下鼠标左键时更改画笔的不透明度为 0.0。  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 有关更完整示例，其中说明了如何对不同类型的画笔进行动画处理，请参阅[画笔示例](https://go.microsoft.com/fwlink/?LinkID=159973)。 有关动画的详细信息，请参阅[动画概述](animation-overview.md)。  
  
 与其他动画示例保持一致，对于此示例中的代码版本使用<xref:System.Windows.Media.Animation.Storyboard>对象来应用它们的动画。 但是，当应用单个动画在代码中的，它是使用更加简便<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法而不是使用<xref:System.Windows.Media.Animation.Storyboard>。 有关示例，请参阅[在不使用情节提要的情况下对属性进行动画处理](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>请参阅

- [动画概述](animation-overview.md)
- [演示图板概述](storyboards-overview.md)
- [画笔示例](https://go.microsoft.com/fwlink/?LinkID=159973)
