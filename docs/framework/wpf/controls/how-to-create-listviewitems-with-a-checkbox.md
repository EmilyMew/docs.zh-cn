---
title: 如何：使用 CheckBox 创建 ListViewItem
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ListView
- controls [WPF], CheckBox
- ListView controls [WPF], CheckBox controls
- CheckBox control [WPF], ListView control
ms.assetid: f6d66c7f-906c-4f65-a55a-0ede9d00e26a
ms.openlocfilehash: b09d5ad11b0961febf524cec1e19cb1e59832e44
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083097"
---
# <a name="how-to-create-listviewitems-with-a-checkbox"></a>如何：使用 CheckBox 创建 ListViewItem
此示例演示如何显示的列<xref:System.Windows.Controls.CheckBox>中的控件<xref:System.Windows.Controls.ListView>控件，它使用<xref:System.Windows.Controls.GridView>。  
  
## <a name="example"></a>示例  
 若要创建包含的列<xref:System.Windows.Controls.CheckBox>中的控件<xref:System.Windows.Controls.ListView>，创建<xref:System.Windows.DataTemplate>，其中包含<xref:System.Windows.Controls.CheckBox>。 然后设置<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>的<xref:System.Windows.Controls.GridViewColumn>到<xref:System.Windows.DataTemplate>。  
  
 下面的示例演示<xref:System.Windows.DataTemplate>，其中包含<xref:System.Windows.Controls.CheckBox>。 该示例将绑定<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A>的属性<xref:System.Windows.Controls.CheckBox>到<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>属性值为<xref:System.Windows.Controls.ListViewItem>包含它。 因此，当<xref:System.Windows.Controls.ListViewItem>，其中包含<xref:System.Windows.Controls.CheckBox>已选中<xref:System.Windows.Controls.CheckBox>检查。  
  
 [!code-xaml[ListViewChkBox#CheckBoxDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#checkboxdatatemplate)]  
  
 下面的示例演示如何创建一列<xref:System.Windows.Controls.CheckBox>控件。 若要将列，该示例设置<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>的属性<xref:System.Windows.Controls.GridViewColumn>到<xref:System.Windows.DataTemplate>。  
  
 [!code-xaml[ListViewChkBox#GridViewColumnCheckBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#gridviewcolumncheckbox)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Control>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView 概述](listview-overview.md)
- [帮助主题](listview-how-to-topics.md)
- [GridView 概述](gridview-overview.md)
