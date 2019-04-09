---
title: 如何：使用 From、To 和 By 控制动画
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 56522ee5bd4391e43c261558b2fa622234c9ea3b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073267"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>如何：使用 From、To 和 By 控制动画
"From/To/By"或"基本动画创建两个目标值之间的转换 (请参阅[动画概述](animation-overview.md)有关不同类型的动画的简介)。 若要设置基本动画的目标值，使用其<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>属性。  下表总结了如何<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>属性可能会一起使用或单独来确定动画的目标值。  
  
|指定的属性|产生的行为|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|从指定的值的动画<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>属性进行动画处理的属性的基值或前一个动画的输出值，具体取决于前一个动画的配置方式。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|从指定的值的动画<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>属性设置为指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>属性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> 和 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|从指定的值的动画<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>之和指定的值的属性<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>属性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|动画继续处理从经过动画处理的属性的基值或前一个动画的输出值与指定的值<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>属性。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|动画从要进行动画处理的属性的基值或前一个动画的输出值和指定的值的总和值<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>属性。|  
  
> [!NOTE]
>  未设置这两<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>属性和<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>在同一个动画的属性。  
  
 若要在两个以上的目标值之间使用内插方法或进行动画处理，请使用关键帧动画。 请参阅[关键帧动画概述](key-frame-animations-overview.md)有关详细信息。  
  
 有关将多个动画应用于单个属性的信息，请参阅[关键帧动画概述](key-frame-animations-overview.md)。  
  
 下面的示例显示了不同设置的效果<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>， <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>，和<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>动画的属性。  
  
## <a name="example"></a>示例  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>请参阅

- [动画概述](animation-overview.md)
- [关键帧动画概述](key-frame-animations-overview.md)
- [从、 To 和 By 动画目标值示例](https://go.microsoft.com/fwlink/?LinkID=159988)
