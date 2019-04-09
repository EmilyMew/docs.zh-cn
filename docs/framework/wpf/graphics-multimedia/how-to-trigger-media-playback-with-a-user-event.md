---
title: 如何：使用用户事件触发媒体播放
ms.date: 03/30/2017
helpviewer_keywords:
- synchronizing media playback with events [WPF]
- playback of media [WPF], synchronizing with events
- media [WPF], synchronizing playback with events
- multimedia [WPF], synchronizing media playback with events
ms.assetid: c4dbe632-6e7f-4d7f-9df5-98737a758bc3
ms.openlocfilehash: ae8ba54cc852bb85350492c95e3e890aebf6534f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150171"
---
# <a name="how-to-trigger-media-playback-with-a-user-event"></a>如何：使用用户事件触发媒体播放
此示例演示如何将媒体播放与事件同步。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Controls.MediaElement>控件和<xref:System.Windows.Media.MediaTimeline>类，以播放声音，当用户单击时发生<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[MediaGallery_snippet#SoundFromUserEventExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/SoundFromUserEventExample.xaml#soundfromusereventexamplewholepage)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.EventTrigger.RoutedEvent%2A>
- <xref:System.Windows.Media.Animation.Storyboard>
- [帮助主题](audio-and-video-how-to-topics.md)
- [图形和多媒体](index.md)
