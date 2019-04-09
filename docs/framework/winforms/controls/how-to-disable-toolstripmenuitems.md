---
title: 如何：禁用 ToolStripMenuItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: a480cd29eef1a79a69f702eed7cd02c28d7ea3de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082719"
---
# <a name="how-to-disable-toolstripmenuitems"></a>如何：禁用 ToolStripMenuItem
您可以限制或扩大用户可通过启用和禁用对用户活动的响应中的菜单项的命令。 菜单项时创建，但这可以通过调整默认情况下启用<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>属性。 在设计时使用此属性可**属性**窗口或以编程方式在代码中设置。  
  
### <a name="to-disable-a-menu-item-programmatically"></a>若要以编程方式禁用菜单项  
  
-   在其中设置菜单项的属性方法中，添加代码以设置<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>属性设置为`false`。  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  禁用菜单中的第一个或顶级菜单项隐藏菜单中包含的所有菜单项，但不会禁用。 同样，禁用具有子菜单项的菜单项隐藏子菜单项，但不会禁用。 如果给定的菜单上的所有命令都都对用户不可用，它视为良好编程习惯，同时隐藏和禁用整个菜单中，这提供了一个清晰的用户界面。 应隐藏和禁用菜单，并禁用每个项目和子菜单项在菜单中，因为仅靠隐藏不会向菜单命令的快捷键通过阻止访问。 设置<xref:System.Windows.Forms.ToolStripItem.Visible%2A>属性的顶级菜单项`false`若要隐藏整个菜单。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [如何：隐藏 ToolStripMenuItem](how-to-hide-toolstripmenuitems.md)
- [MenuStrip 控件概述](menustrip-control-overview-windows-forms.md)
