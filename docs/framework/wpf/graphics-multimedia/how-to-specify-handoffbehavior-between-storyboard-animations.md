---
title: 如何：指定情节提要动画之间的 HandoffBehavior
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: d7129d6a48bdf31dc4953bb450267ad3b38fdd17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083876"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>如何：指定情节提要动画之间的 HandoffBehavior
此示例演示如何指定演示图板动画之间的切换行为。 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>属性的<xref:System.Windows.Media.Animation.BeginStoryboard>指定新动画已应用于属性的任何现有与之交互。  
  
## <a name="example"></a>示例  
 以下示例创建两个按钮放大鼠标光标移动到它们上方时，将光标移开时变得更小。 如果将鼠标移到一个按钮，然后快速删除光标，第一个完成之前，将应用第二个动画。 像这样，您可以看到之间的差异的两个动画重叠时，它是<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>的值<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>和<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>。 值为<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>结合了导致由于可以顺利过渡动画时的值之间的重叠动画<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>使新动画立即替换之前的重叠的动画。  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [动画概述](animation-overview.md)
- [动画和计时帮助主题](animation-and-timing-how-to-topics.md)
