---
title: 如何：使用 Windows 窗体 ContextMenu 组件添加和移除菜单项
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
ms.openlocfilehash: e02a187edc1392f15fe98354bb2e5c43843e430c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094458"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>如何：使用 Windows 窗体 ContextMenu 组件添加和移除菜单项
介绍如何添加和删除 Windows 窗体中的快捷菜单项。  
  
 Windows 窗体<xref:System.Windows.Forms.ContextMenu>组件提供了与所选对象相关的常用命令的菜单。 您可以通过添加到快捷菜单添加项<xref:System.Windows.Forms.MenuItem>对象添加到<xref:System.Windows.Forms.Menu.MenuItems%2A>集合。  
  
 你可以永久移除项的快捷菜单;但是，在运行时可能会隐藏或禁用项改为更适合。  
  
> [!IMPORTANT]
>  尽管<xref:System.Windows.Forms.MenuStrip>和<xref:System.Windows.Forms.ContextMenuStrip>替换并将功能添加到<xref:System.Windows.Forms.MainMenu>并<xref:System.Windows.Forms.ContextMenu>的早期版本中，控件<xref:System.Windows.Forms.MainMenu>和<xref:System.Windows.Forms.ContextMenu>也可选择将保留向后兼容性和将来使用。  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>若要从快捷菜单中删除项目  
  
1.  使用<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>或<xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>方法<xref:System.Windows.Forms.Menu.MenuItems%2A>的集合<xref:System.Windows.Forms.ContextMenu>组件中移除特定菜单项。  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     或  
  
2.  使用`Clear`方法`MenuItems`的集合<xref:System.Windows.Forms.ContextMenu>组件以从菜单中删除所有项。  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ContextMenu>
- [ContextMenu 组件](contextmenu-component-windows-forms.md)
- [ContextMenu 组件概述](contextmenu-component-overview-windows-forms.md)
