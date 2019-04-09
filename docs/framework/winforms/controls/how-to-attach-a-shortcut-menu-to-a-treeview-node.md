---
title: 如何：将快捷菜单附加到 TreeView 节点
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: ba29e86f62c8d56b0d300d1841a70f434087dd84
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100011"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>如何：将快捷菜单附加到 TreeView 节点
Windows 窗体<xref:System.Windows.Forms.TreeView>控件显示节点，类似于文件和文件夹显示在 Windows 资源管理器的左窗格中的层次结构。 通过设置<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>属性，您可以区分上下文的操作向用户提供他们右键单击时<xref:System.Windows.Forms.TreeView>控件。 通过将相关联<xref:System.Windows.Forms.ContextMenuStrip>组件与单个<xref:System.Windows.Forms.TreeNode>项，可以添加到快捷菜单上功能的自定义的级别应用<xref:System.Windows.Forms.TreeView>控件。  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>要以编程方式与树节点关联的快捷菜单  
  
1.  实例化<xref:System.Windows.Forms.TreeView>控件的相应属性设置，创建一个根<xref:System.Windows.Forms.TreeNode>，以及如何将子节点。  
  
2.  实例化<xref:System.Windows.Forms.ContextMenuStrip>组件，以及如何将<xref:System.Windows.Forms.ToolStripMenuItem>为想要在运行时提供每个操作。  
  
3.  设置<xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A>属性的相应<xref:System.Windows.Forms.TreeNode>到你创建的快捷菜单。  
  
4.  当设置此属性时，右键单击节点时，将显示的快捷菜单。  
  
 下面的代码示例将创建一个基本<xref:System.Windows.Forms.TreeView>并<xref:System.Windows.Forms.ContextMenuStrip>与根关联<xref:System.Windows.Forms.TreeNode>的<xref:System.Windows.Forms.TreeView>。 将需要自定义菜单选项为适合<xref:System.Windows.Forms.TreeView>进行开发。 此外，你将想要编写代码来处理<xref:System.Windows.Forms.ToolStripItem.Click>这些菜单项的事件。  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ContextMenuStrip>
- [TreeView 控件](treeview-control-windows-forms.md)
