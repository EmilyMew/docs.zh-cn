---
title: 如何：使用设计器隐藏 ToolStripMenuItem
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: ddfbcbe78cdf8e5b0d126e82189589edef2be58a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085683"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>如何：使用设计器隐藏 ToolStripMenuItem
隐藏菜单项是一种方法来控制你的应用程序的用户界面 (UI) 和限制用户命令。 通常情况下，想要在其上的菜单项都不可用时隐藏整个菜单。 这提供了用户很少会分心。 此外，您可能希望能够同时隐藏和禁用的菜单或菜单项，如仅隐藏不会阻止用户使用的快捷键访问菜单命令。 禁用菜单项的详细信息，请参阅[如何：使用设计器禁用 Toolstripmenuitem](how-to-disable-toolstripmenuitems-using-the-designer.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>若要隐藏顶级菜单及其子菜单项  
  
1.  选择的顶级菜单项并设置其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>或<xref:System.Windows.Forms.ToolStripItem.Available%2A>属性设置为`false`。  
  
     在隐藏的顶级菜单项时，也会隐藏该菜单中的所有菜单项。 如果单击以外某处上<xref:System.Windows.Forms.MenuStrip>设置之后<xref:System.Windows.Forms.ToolStripItem.Visible%2A>到`false`，将整个顶级菜单项和及其子菜单项从窗体中，从而向您展示你的操作的运行效果中消失。 若要在设计时显示隐藏的顶级菜单项，请单击<xref:System.Windows.Forms.MenuStrip>中**组件栏**，在**文档大纲**，或在属性网格的顶部。  
  
> [!NOTE]
>  很少会隐藏整个菜单合并方案中的多文档界面 (MDI) 子菜单除外。  
  
### <a name="to-hide-a-submenu-item"></a>若要隐藏子菜单项  
  
1.  选择的子菜单项并设置其<xref:System.Windows.Forms.ToolStripItem.Visible%2A>属性设置为`false`。  
  
     在隐藏子菜单项时，它仍显示在设计时窗体上，以便可以轻松地选择它来进一步的工作。 它将实际被隐藏在运行时。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [MenuStrip 控件概述](menustrip-control-overview-windows-forms.md)
- [如何：使用设计器禁用 ToolStripMenuItem](how-to-disable-toolstripmenuitems-using-the-designer.md)
