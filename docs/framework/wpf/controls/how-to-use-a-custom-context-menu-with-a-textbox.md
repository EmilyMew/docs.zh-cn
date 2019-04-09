---
title: 如何：将自定义上下文菜单与 TextBox 结合使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: b0507c6fa37f0f51f9e12ebe5f908c39c25b50d9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129410"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>如何：将自定义上下文菜单与 TextBox 结合使用
此示例演示如何定义和实现的简单自定义上下文菜单<xref:System.Windows.Controls.TextBox>。  
  
## <a name="example"></a>示例  
 以下[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]的示例定义了<xref:System.Windows.Controls.TextBox>包括自定义上下文菜单的控件。  
  
 使用定义的上下文菜单<xref:System.Windows.Controls.ContextMenu>元素。  本身的上下文菜单包含一系列<xref:System.Windows.Controls.MenuItem>元素和<xref:System.Windows.Controls.Separator>元素。  每个<xref:System.Windows.Controls.MenuItem>元素定义了一个命令在上下文菜单中;<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>属性定义菜单命令的显示文本和<xref:System.Windows.Controls.MenuItem.Click>属性指定每个菜单项的处理程序方法。  <xref:System.Windows.Controls.Separator>元素只会促使要呈现的前面与后面的菜单项之间的分隔行。  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>示例  
 下面的示例显示了前面的上下文菜单定义中，实现代码以及启用和禁用上下文菜单的代码。  <xref:System.Windows.Controls.ContextMenu.Opened>事件用来动态地启用或禁用某些命令，具体取决于当前状态的<xref:System.Windows.Controls.TextBox>。  
  
 若要还原默认的上下文菜单，请使用<xref:System.Windows.DependencyObject.ClearValue%2A>方法来清除的值<xref:System.Windows.FrameworkElement.ContextMenu%2A>属性。  若要完全禁用上下文菜单，设置<xref:System.Windows.FrameworkElement.ContextMenu%2A>属性设置为 null 引用 (`Nothing`在 Visual Basic 中)。  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>请参阅

- [将拼写检查功能与上下文菜单结合使用](how-to-use-spell-checking-with-a-context-menu.md)
- [TextBox 概述](textbox-overview.md)
- [RichTextBox 概述](richtextbox-overview.md)
