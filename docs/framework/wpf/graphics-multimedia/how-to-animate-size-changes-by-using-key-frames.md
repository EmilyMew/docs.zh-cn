---
title: 如何：使用关键帧对大小变化进行动画处理
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: a7adb16297f50e191628344d7e25d41f38a97861
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180227"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>如何：使用关键帧对大小变化进行动画处理
此示例演示如何使用关键帧对大小变化进行动画处理。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>类进行动画处理<xref:System.Windows.Media.ArcSegment.Size%2A>属性的<xref:System.Windows.Media.ArcSegment>。 此动画按以下方式使用三个关键帧：  
  
1.  在动画的前半秒，使用的实例<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>类，以逐渐增加弧的大小。之类的线性关键帧<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>创建值之间平滑的线性转换。  
  
2.  在下一步末尾前半秒中，使用的实例<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>类突然增加弧的大小。之类的离散关键帧<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>之间创建突然跳跃的值，即，大小变化突然发生，而不是。  
  
3.  通过最后两秒内，使用的实例<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>类，以增加弧的大小。之类的自由绘制曲线关键帧<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>创建根据的值在值之间的变量转换<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>属性。 在本例中，弧的大小开始时缓慢增加，然后以指数方式增加，直到时间段结束。  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 有关完整示例，请参阅[关键帧动画示例](https://go.microsoft.com/fwlink/?LinkID=160012)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [关键帧动画概述](key-frame-animations-overview.md)
- [关键帧操作说明主题](key-frame-animation-how-to-topics.md)
