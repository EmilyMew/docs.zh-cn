---
title: 如何：使用设计器向 ToolBar 控件添加按钮
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: 133190426229a10ed6f637293326c229e808bfdb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084019"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>如何：使用设计器向 ToolBar 控件添加按钮
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> 控件取代了 <xref:System.Windows.Forms.ToolBar> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.ToolBar> 控件以实现向后兼容并供将来使用。  
  
 不可或缺的一部分<xref:System.Windows.Forms.ToolBar>控件是您向其中添加的按钮。 这些可用于提供方便您访问菜单命令或者，或者，您可以将它们放在另一个区域中的应用程序以向你的菜单结构中不可用的用户公开的命令的用户界面。  
  
 下面的过程需要**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.ToolBar>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-buttons-at-design-time"></a>若要在设计时添加按钮  
  
1.  选择 <xref:System.Windows.Forms.ToolBar> 控件。  
  
2.  在中**属性**窗口中，单击<xref:System.Windows.Forms.ToolBar.Buttons%2A>属性来选择它，然后单击**省略号**(![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 按钮以打开**工具栏按钮集合编辑器**。  
  
3.  使用**外**并**删除**按钮来添加和删除按钮从<xref:System.Windows.Forms.ToolBar>控件。  
  
4.  配置中的各个按钮的属性**属性**编辑器右侧的窗格中显示的窗口。 下表显示了需要考虑一些重要属性。  
  
    |属性|描述|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|设置要在下拉工具栏按钮中显示的菜单。 工具栏按钮<xref:System.Windows.Forms.ToolBarButton.Style%2A>属性必须设置为<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>。 此属性采用的实例<xref:System.Windows.Forms.ContextMenu>作为引用的类。|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|设置是否为部分按下切换式工具栏按钮。 工具栏按钮<xref:System.Windows.Forms.ToolBarButton.Style%2A>属性必须设置为<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>。|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|设置是否切换式工具栏按钮当前处于按下状态。 工具栏按钮<xref:System.Windows.Forms.ToolBarButton.Style%2A>属性必须设置为<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>或<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>。|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|将工具栏按钮的样式设置。 必须是中的值之一<xref:System.Windows.Forms.ToolBarButtonStyle>枚举。|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|显示按钮的文本字符串。|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|显示为按钮的工具提示文本。|  
  
5.  单击**确定**以关闭对话框并创建您指定的面板。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ToolBar>
- [如何：定义工具栏按钮的图标](how-to-define-an-icon-for-a-toolbar-button.md)
- [如何：触发工具栏按钮的菜单事件](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar 控件概述](toolbar-control-overview-windows-forms.md)
- [ToolBar 控件](toolbar-control-windows-forms.md)
