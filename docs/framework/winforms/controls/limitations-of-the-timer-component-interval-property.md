---
title: Windows 窗体 Timer 组件的 Interval 属性的限制
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 54782c4e0460ba1ba9b8a870b8f60f08a76340b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125167"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Windows 窗体 Timer 组件的 Interval 属性的限制
Windows 窗体<xref:System.Windows.Forms.Timer>组件具有<xref:System.Windows.Forms.Timer.Interval%2A>属性，它指定一个计时器事件和下一步之间传递的毫秒数。 除非禁用该组件，计时器会继续接收<xref:System.Windows.Forms.Timer.Tick>事件的时间大致相同时间间隔。  
  
 此组件专为 Windows 窗体环境设计。 如果需要适合服务器环境的计时器，请参阅[基于服务器的计时器介绍](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。  
  
## <a name="the-interval-property"></a>间隔属性  
 <xref:System.Windows.Forms.Timer.Interval%2A>属性有一些限制需要考虑进行编程时<xref:System.Windows.Forms.Timer>组件：  
  
-   如果你的应用程序或其他应用程序在系统上进行大量需求 — 例如长循环、 大量的计算或驱动器、 网络或端口访问 — 你的应用程序可能无法获得的计时器事件，通常为<xref:System.Windows.Forms.Timer.Interval%2A>属性指定。  
  
-   不保证所精确经过的时间间隔。 若要确保准确性，计时器应检查系统时钟根据需要而不是尝试进行内部跟踪的累计的时间。  
  
-   精度为<xref:System.Windows.Forms.Timer.Interval%2A>属性是以毫秒为单位。 某些计算机提供的高分辨率计数器，分辨率高于毫秒。 此类计数器的可用性取决于您的计算机的处理器硬件。
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Timer>
- [Timer 组件](timer-component-windows-forms.md)
- [Timer 组件概述](timer-component-overview-windows-forms.md)
