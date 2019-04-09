---
title: StatusBar 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 5fdefa7d7e7c7ef543f677be7beb61dfee54e077
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077311"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar 控件概述（Windows 窗体）
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>并<xref:System.Windows.Forms.ToolStripStatusLabel>控件替换，并将功能添加到<xref:System.Windows.Forms.StatusBar>并<xref:System.Windows.Forms.StatusBarPanel>控制; 但是，<xref:System.Windows.Forms.StatusBar>和<xref:System.Windows.Forms.StatusBarPanel>控件将保留用于向后兼容性并供将来使用，如果你选择。  
  
 Windows 窗体[StatusBar 控件](statusbar-control-windows-forms.md)窗体上用作区域，通常显示在底部窗口中，应用程序可以在其中显示各种类型的状态信息。 <xref:System.Windows.Forms.StatusBar> 控件可以具有状态栏面板上显示的文本或图标，用于指示状态或一系列的动画中的图标指示进程正在运行;例如， [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] ，该值指示保存该文档。  
  
## <a name="using-the-statusbar-control"></a>使用 StatusBar 控件  
 Internet Explorer 使用状态栏来指示当鼠标滚动超链接; 时的页的 URL[!INCLUDE[ofprword](../../../../includes/ofprword-md.md)]为您提供信息页的位置、 部分位置和编辑模式，例如改写和修订跟踪; 以及 Visual Studio 使用状态栏提供上下文相关的信息，例如告诉您如何操作可停靠窗口为停靠或浮动。  
  
 可以在状态栏上显示一条消息，通过设置<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>属性设置为`false`（默认值） 和设置<xref:System.Windows.Forms.StatusBar.Text%2A>到你想要在状态栏中显示的文本的状态栏的属性。 可以将状态栏划分为多个面板，以通过设置显示的信息的多个类型<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>属性设置为`true`并使用<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A>方法的<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [如何：确定 Windows 窗体 StatusBar 控件中被单击的面板](determine-which-panel-wf-statusbar-control-was-clicked.md)
