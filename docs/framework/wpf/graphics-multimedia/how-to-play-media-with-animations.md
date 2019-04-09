---
title: 如何：播放带有动画的媒体
ms.date: 03/30/2017
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
ms.openlocfilehash: 200f9d62c67a02088fe5a5789cdb41a04837d430
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079898"
---
# <a name="how-to-play-media-with-animations"></a>如何：播放带有动画的媒体
此示例演示如何通过使用在同一时间播放媒体和动画<xref:System.Windows.Media.MediaTimeline>并<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>中相同的类<xref:System.Windows.Media.Animation.Storyboard>。  
  
## <a name="example"></a>示例  
 可以使用一个或多个<xref:System.Windows.Media.MediaTimeline>中的对象<xref:System.Windows.Media.Animation.Storyboard>与其他<xref:System.Windows.Media.Animation.Timeline>对象，例如动画。  
  
 下面的示例设置<xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>的属性<xref:System.Windows.Media.Animation.Storyboard>的值为`Slip`，它指定动画不播放之前在媒体 （在此示例中为视频） 进行。 如果媒体播放因加载时间而延迟，可能需要此功能。  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>
- [帮助主题](audio-and-video-how-to-topics.md)
- [演示图板概述](storyboards-overview.md)
- [关键帧动画概述](key-frame-animations-overview.md)
- [动画概述](animation-overview.md)
- [图形和多媒体](index.md)
