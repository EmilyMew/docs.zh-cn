---
title: 如何：使用关键帧对点进行动画处理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: 2e34ba035c8d7f9132915a9269d545f32033cbed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132582"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>如何：使用关键帧对点进行动画处理
此示例演示如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>类进行动画处理<xref:System.Windows.Point>。  
  
## <a name="example"></a>示例  
 以下示例沿三角形路径移动椭圆形。 该示例使用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>类进行动画处理<xref:System.Windows.Media.EllipseGeometry.Center%2A>属性的<xref:System.Windows.Media.EllipseGeometry>。 此动画按以下方式使用三个关键帧：  
  
1.  在前半秒中，使用的实例<xref:System.Windows.Media.Animation.LinearPointKeyFrame>类将椭圆形沿路径以稳定速率从其起始位置。 之类的线性关键帧<xref:System.Windows.Media.Animation.LinearPointKeyFrame>创建值之间平滑的线性插值。  
  
2.  在结束时的下一个前半秒中，使用的实例<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>类将椭圆形沿路径突然移动到下一个位置。 之类的离散关键帧<xref:System.Windows.Media.Animation.DiscretePointKeyFrame>值之间创建突然跳跃。  
  
3.  在最后两秒内，使用的实例<xref:System.Windows.Media.Animation.SplinePointKeyFrame>类将椭圆形移回其起始位置。 之类的自由绘制曲线关键帧<xref:System.Windows.Media.Animation.SplinePointKeyFrame>创建根据的值在值之间的变量转换<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A>属性。 在此示例中，动画开始时较为缓慢，然后以指数方式加速，直到时间段结束。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 有关完整示例，请参阅[关键帧动画示例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
 与其他动画示例保持一致，对于此示例中的代码版本使用<xref:System.Windows.Media.Animation.Storyboard>对象来应用<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>。 但是，当应用单个动画在代码中的，它是使用更加简便<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法而不是使用<xref:System.Windows.Media.Animation.Storyboard>。 有关示例，请参阅[在不使用情节提要的情况下对属性进行动画处理](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [关键帧动画概述](key-frame-animations-overview.md)
- [关键帧操作说明主题](key-frame-animation-how-to-topics.md)
