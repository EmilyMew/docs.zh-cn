---
title: 如何：使用关键帧对边框的粗细进行动画处理
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 0c5dc61ac1a4cc3f2aba83ac3a4a71084b553a2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087347"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>如何：使用关键帧对边框的粗细进行动画处理
此示例演示如何进行动画处理<xref:System.Windows.Controls.Control.BorderThickness%2A>属性的<xref:System.Windows.Controls.Border>。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>类进行动画处理<xref:System.Windows.Controls.Control.BorderThickness%2A>属性的<xref:System.Windows.Controls.Border>。 此动画按以下方式使用三个关键帧：  
  
1.  在前半秒中，使用的实例<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>类，以逐渐增加边框的粗细。 该示例使用<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>创建值之间平滑的线性递增。  
  
2.  在下一步末尾前半秒中，使用的实例<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>类突然增加边框的粗细。 离散关键帧，如派生自<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>之间创建突然跳跃的值，也就是说，动画的运动是不平稳。  
  
3.  在最后两秒内，使用的实例<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>类，以减小边框的粗细。 自由绘制曲线关键帧，如派生自<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>创建根据的值在值之间的变量转换<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A>属性。 在此关键帧中，动画开始时缓慢，然后以指数方式加速，直到时间段结束。  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 有关完整示例，请参阅[关键帧动画示例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [关键帧动画概述](key-frame-animations-overview.md)
- [关键帧操作说明主题](key-frame-animation-how-to-topics.md)
- [对 BorderThickness 值进行动画处理](../controls/how-to-animate-a-borderthickness-value.md)
