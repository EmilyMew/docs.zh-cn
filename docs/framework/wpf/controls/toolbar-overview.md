---
title: ToolBar 概述
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 711d55e46fb548787976a1f966c9fbf6dc7f12d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105321"
---
# <a name="toolbar-overview"></a>ToolBar 概述
<xref:System.Windows.Controls.ToolBar> 控件是一组命令或控件通常在功能上相关的容器。 一个<xref:System.Windows.Controls.ToolBar>通常包含调用命令的按钮。  

<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar 控件  
 <xref:System.Windows.Controls.ToolBar>控件采用从到单个行或列的按钮或其他控件栏类似于排列其名称。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> 控件提供一种溢出机制的任意大小约束中执行操作无法自然容纳的项放<xref:System.Windows.Controls.ToolBar>到特殊的溢出区域。 此外， [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar>控件通常用于与相关<xref:System.Windows.Controls.ToolBarTray>提供特殊的布局行为，以及支持用于用户启动的大小和排列工具栏的控件。  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>在 ToolBarTray 中指定 ToolBar 位置  
 使用<xref:System.Windows.Controls.ToolBar.Band%2A>并<xref:System.Windows.Controls.ToolBar.BandIndex%2A>属性来定位<xref:System.Windows.Controls.ToolBar>中<xref:System.Windows.Controls.ToolBarTray>。 <xref:System.Windows.Controls.ToolBar.Band%2A> 指示在其中的位置<xref:System.Windows.Controls.ToolBar>放置在其父<xref:System.Windows.Controls.ToolBarTray>。 <xref:System.Windows.Controls.ToolBar.BandIndex%2A> 指示在其中顺序<xref:System.Windows.Controls.ToolBar>其区段内放置。 下面的示例演示如何使用此属性将<xref:System.Windows.Controls.ToolBar>控件内<xref:System.Windows.Controls.ToolBarTray>。  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>带有溢出项的 ToolBar  
 通常<xref:System.Windows.Controls.ToolBar>控件包含更多的项不是可以适合于工具栏的大小。 在此情况下，<xref:System.Windows.Controls.ToolBar>显示溢出按钮。 若要查看溢出项，用户单击了溢出按钮，并且这些项将显示在下方的弹出窗口中<xref:System.Windows.Controls.ToolBar>。 下图显示<xref:System.Windows.Controls.ToolBar>带有溢出项：  
  
 ![显示带有溢出项的工具栏的屏幕截图。](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 您可以指定工具栏上的项当通过设置在溢出面板上放置<xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType>附加属性设置为<xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>， <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>，或<xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>。 以下示例指定工具栏上的最后四个按钮应始终在溢出面板上。  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 <xref:System.Windows.Controls.ToolBar>使用<xref:System.Windows.Controls.Primitives.ToolBarPanel>和一个<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>中其<xref:System.Windows.Controls.ControlTemplate>。  <xref:System.Windows.Controls.Primitives.ToolBarPanel>负责在工具栏上的项的布局。  <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>负责无法容纳的项的布局<xref:System.Windows.Controls.ToolBar>。 有关的示例<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.ToolBar>，请参阅  
  
 [ToolBar 样式和模板](toolbar-styles-and-templates.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [设置 ToolBar 上控件的样式](how-to-style-controls-on-a-toolbar.md)
- [WPF 控件库示例](https://go.microsoft.com/fwlink/?LinkID=160053)
