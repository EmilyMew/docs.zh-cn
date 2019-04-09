---
title: 如何：使用关键帧对颜色进行动画处理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: d911b1f14cf71aebf95b566eb710fec8ec9e2a29
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095162"
---
# <a name="how-to-animate-color-by-using-key-frames"></a>如何：使用关键帧对颜色进行动画处理
此示例演示如何进行动画处理<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>使用关键帧。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>类进行动画处理<xref:System.Windows.Media.SolidColorBrush.Color%2A>属性的<xref:System.Windows.Media.SolidColorBrush>。 此动画按以下方式使用三个关键帧：  
  
1.  在前两秒中，使用的实例<xref:System.Windows.Media.Animation.LinearColorKeyFrame>类，以逐渐更改颜色从绿色到红色。 之类的线性关键帧<xref:System.Windows.Media.Animation.LinearColorKeyFrame>创建值之间平滑的线性转换。  
  
2.  在结束时的下一个前半秒中，使用的实例<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>类快速将颜色从红色更改为黄色。 之类的离散关键帧<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame>之间创建突然变化的值，也就是说，此部分动画的颜色变化快速发生，而不是。  
  
3.  在最后两秒内，使用的实例<xref:System.Windows.Media.Animation.SplineColorKeyFrame>类，以再次更改颜色，这一次从黄色变回绿色。 之类的自由绘制曲线关键帧<xref:System.Windows.Media.Animation.SplineColorKeyFrame>创建根据的值在值之间的变量转换<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A>属性。 在此示例中，颜色变化开始时缓慢，然后以指数方式加速，直到时间段结束。  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 有关完整示例，请参阅[关键帧动画示例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [关键帧动画概述](key-frame-animations-overview.md)
- [关键帧操作说明主题](key-frame-animation-how-to-topics.md)
