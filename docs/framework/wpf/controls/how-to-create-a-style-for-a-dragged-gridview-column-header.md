---
title: 如何：创建拖动的 GridView 列标头的样式
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
ms.openlocfilehash: dbcdd38e0397b8e637aff962420a2959f33203df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090090"
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>如何：创建拖动的 GridView 列标头的样式
此示例演示如何更改外观的拖动<xref:System.Windows.Controls.GridViewColumnHeader>当用户更改的列位置。  
  
## <a name="example"></a>示例  
 当将列标题拖到其他位置<xref:System.Windows.Controls.ListView>，它使用<xref:System.Windows.Controls.GridView>作为其视图模式，在列移至新位置。 当您拖动列标题时，标头的浮点副本会显示除了原始标头。 中的列标题<xref:System.Windows.Controls.GridView>为由<xref:System.Windows.Controls.GridViewColumnHeader>对象。  
  
 若要自定义这两个浮点型和原始标头的外观，可以设置<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>修改<xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>。 这些<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>时应用<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>属性值是`true`并且<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>属性值是<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。  
  
 当用户按下鼠标左键和鼠标悬停在按住<xref:System.Windows.Controls.GridViewColumnHeader>，则<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>属性值更改为`true`。 同样，当用户开始拖动操作时，才<xref:System.Windows.Controls.GridViewColumnHeader.Role%2A>属性更改为<xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>。  
  
 下面的示例演示如何设置<xref:System.Windows.Controls.ControlTemplate.Triggers%2A>若要更改<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.Background%2A>原始窗口和浮动的标头时用户将列拖至新位置的颜色。  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [帮助主题](listview-how-to-topics.md)
- [ListView 概述](listview-overview.md)
- [GridView 概述](gridview-overview.md)
