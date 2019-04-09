---
title: 如何：冻结 Windows 窗体 DataGridView 控件中的列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: a0b77a7356b09a5cc95ec165a62c45852f542b8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187417"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>如何：冻结 Windows 窗体 DataGridView 控件中的列
用户查看 Windows 窗体 <xref:System.Windows.Forms.DataGridView> 控件中显示的数据时，有时需要频繁地引用单个列或列集。 例如，显示包含许多列的客户信息表时，使其他列可在可使区域外滚动的同时始终显示客户姓名非常有用。  
  
 若要实现此行为，可冻结控件中的列。 冻结列时，也将冻结其左侧（在从右到左的语言脚本中为右侧）的所有列。 冻结的列保持不变，而所有其他列可以滚动。  
  
> [!NOTE]
>  如果启用了列重新排序，冻结的列被视为一组不同于未冻结的列。 用户可重新定位任一组中的列，但不能将列从一个组移到另一组。  
  
 列的 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> 属性决定列在网格内是否始终可见。  
  
 Visual Studio 中对此任务提供支持。  另请参阅[如何：冻结列在 Windows 窗体 DataGridView 控件使用设计器](freeze-columns-in-the-datagrid-using-the-designer.md)。  
  
### <a name="to-freeze-a-column-programmatically"></a>以编程方式冻结列  
  
-   将 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> 属性设置为 `true`。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件，其包含一个名为 `AddToCartButton` 的列。  
  
-   对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Windows 窗体 DataGridView 控件中的基本列、行和单元格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [如何：启用 Windows 窗体 DataGridView 控件中列的重新排序](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
