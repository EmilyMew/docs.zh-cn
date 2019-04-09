---
title: 如何：使用 Windows 窗体 ListView 控件在列中显示子项
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: defa8aa736927c9076eb2410d6d914a8f7550d03
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183711"
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>如何：使用 Windows 窗体 ListView 控件在列中显示子项
Windows 窗体<xref:System.Windows.Forms.ListView>控件可以显示其他文本或子项的详细信息视图中的每个项。 第一列显示项文本，如雇员编号。 第二个，第三个和后续的列将显示第一天，第二，并随后的关联子项。  
  
### <a name="to-add-subitems-to-a-list-item"></a>若要将子项添加到列表项  
  
1.  添加所需的任何列。 由于第一列将显示项的<xref:System.Windows.Forms.ListView.Text%2A>属性，您需要一个更多的列多于存在的子项。 添加列的详细信息，请参阅[如何：列到 Windows 窗体 ListView 控件添加](how-to-add-columns-to-the-windows-forms-listview-control.md)。  
  
2.  调用<xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A>方法返回的集合<xref:System.Windows.Forms.ListViewItem.SubItems%2A>项的属性。 下面的代码示例设置的员工姓名和部门联系，获取一个列表项。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>请参阅

- [ListView 控件概述](listview-control-overview-windows-forms.md)
- [如何：使用 Windows 窗体 ListView 控件添加和移除项](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [如何：向 Windows 窗体 ListView 控件中添加列](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [如何：显示 Windows 窗体 ListView 控件的图标](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [如何：向 TreeView 或 ListView 控件添加自定义信息（Windows 窗体）](add-custom-information-to-a-treeview-or-listview-control-wf.md)
