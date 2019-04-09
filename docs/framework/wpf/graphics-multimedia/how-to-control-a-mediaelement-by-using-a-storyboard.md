---
title: 如何：使用情节提要控制 MediaElement
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
ms.openlocfilehash: ae785e11b1da0f2c408b24021ad46ab071419378
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100309"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>如何：使用情节提要控制 MediaElement
此示例演示如何控制<xref:System.Windows.Controls.MediaElement>通过使用<xref:System.Windows.Media.MediaTimeline>中<xref:System.Windows.Media.Animation.Storyboard>。  
  
## <a name="example"></a>示例  
 当你使用<xref:System.Windows.Media.MediaTimeline>中<xref:System.Windows.Media.Animation.Storyboard>控制的计时<xref:System.Windows.Controls.MediaElement>，功能是相同的功能的其他<xref:System.Windows.Media.Animation.Timeline>对象，例如动画。 例如，<xref:System.Windows.Media.MediaTimeline>使用<xref:System.Windows.Media.Animation.Timeline>属性，如<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>属性来指定何时开始<xref:System.Windows.Controls.MediaElement>（启动媒体的播放）。 它还使用<xref:System.Windows.Media.Animation.Timeline.Duration%2A>属性来指定多长时间<xref:System.Windows.Controls.MediaElement>处于活动状态 （的媒体的播放持续时间）。 有关使用详细信息<xref:System.Windows.Media.Animation.Timeline>对象与<xref:System.Windows.Media.Animation.Storyboard>，请参阅[情节提要概述](storyboards-overview.md)。  
  
 此示例演示如何创建简单的媒体播放器使用<xref:System.Windows.Media.MediaTimeline>来控制播放。 Media player 还包括播放、 暂停、 继续和停止按钮。 播放机也有<xref:System.Windows.Controls.Slider>充当一个进度栏控件。  
  
 下面的示例创建[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]媒体播放器。  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 以下示例创建进度栏的功能。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [控制 MediaElement（播放、暂停、停止、音量和速度）](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [演示图板概述](storyboards-overview.md)
- [关键帧动画概述](key-frame-animations-overview.md)
- [动画概述](animation-overview.md)
- [帮助主题](audio-and-video-how-to-topics.md)
- [图形和多媒体](index.md)
