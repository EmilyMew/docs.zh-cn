---
title: ContextMenu 组件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090558"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu 组件概述（Windows 窗体）
> [!IMPORTANT]
>  尽管<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>替换并将功能添加到<xref:System.Windows.Forms.MainMenu>并<xref:System.Windows.Forms.ContextMenu>的早期版本中，控件<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>也可选择将保留向后兼容性和将来使用。  
  
 使用 Windows 窗体<xref:System.Windows.Forms.ContextMenu>组件，您可以向用户提供与所选对象相关联的常用命令的轻松访问的快捷菜单。 快捷菜单中的项通常是从主应用程序中的其他位置出现的菜单项的子集。 用户通常可以通过右键单击鼠标访问快捷菜单。 在 Windows 窗体上快捷菜单是与控件相关联。  
  
## <a name="key-properties"></a>键属性  
 可以与控件关联的快捷菜单，通过设置控件的<xref:System.Windows.Forms.Control.ContextMenu%2A>属性设置为<xref:System.Windows.Forms.ContextMenu>组件。 一个快捷方式菜单可以与多个控件相关联，但每个控件可以有一个快捷方式菜单。  
  
 键属性<xref:System.Windows.Forms.ContextMenu>组件是<xref:System.Windows.Forms.Menu.MenuItems%2A>属性。 可以通过以编程方式创建添加菜单项<xref:System.Windows.Forms.MenuItem>对象并将它们添加到<xref:System.Windows.Forms.Menu.MenuItemCollection>的快捷菜单。 因为快捷菜单中的项通常取自其他菜单，您将最常添加项到快捷菜单通过将其复制。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
