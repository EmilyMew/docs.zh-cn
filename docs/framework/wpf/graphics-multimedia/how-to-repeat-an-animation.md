---
title: 如何：重复动画
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: a80f72b0e67c13890d4befcbd5ab7c4a92a93fe7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150535"
---
# <a name="how-to-repeat-an-animation"></a>如何：重复动画
此示例演示如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>属性的<xref:System.Windows.Media.Animation.Timeline>为了控制动画的重复行为。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>属性的<xref:System.Windows.Media.Animation.Timeline>控制动画重复其简单持续时间的次数。 通过使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>，可以指定<xref:System.Windows.Media.Animation.Timeline>重复特定次数 （迭代计数） 或指定的时间段内。 在任一情况下，动画将经历填充请求的计数或持续时间所需的任意多个开始到结束运行。  
  
 默认情况下，时间线具有值为 1.0，这意味着它们播放一次，不进行重复的重复计数。 但是，如果您设置<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>的属性<xref:System.Windows.Media.Animation.Timeline>到<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，无限期地重复时间线。  
  
 下面的示例演示如何使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>属性来控制动画的重复行为。 该示例进行动画处理<xref:System.Windows.FrameworkElement.Width%2A>的每个矩形使用不同类型的重复行为的五个矩形的属性。  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 有关完整示例，请参阅[动画计时行为示例](https://go.microsoft.com/fwlink/?LinkID=159970)。  
  
## <a name="see-also"></a>请参阅

- [在重复循环过程中累积动画值](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [指定时间线是否自动反转](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [动画和计时帮助主题](animation-and-timing-how-to-topics.md)
- [动画概述](animation-overview.md)
- [动画计时行为示例](https://go.microsoft.com/fwlink/?LinkID=159970)
