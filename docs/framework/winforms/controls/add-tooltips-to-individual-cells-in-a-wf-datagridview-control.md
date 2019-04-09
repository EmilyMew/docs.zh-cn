---
title: 如何：为 Windows 窗体 DataGridView 控件中的各个单元格添加工具提示
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: 3307c92a13e5730de6dce0fe45b924e44b7af554
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119634"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a>如何：为 Windows 窗体 DataGridView 控件中的各个单元格添加工具提示
默认情况下，使用工具提示显示的值<xref:System.Windows.Forms.DataGridView>太小而无法显示其完整内容的单元格。 您可以重写此行为，但是，若要设置的各个单元格工具提示文本值。 这是要显示给用户的单元的相关的其他信息，或向用户提供的单元格内容的其他说明。 例如，如果有行显示状态图标，你可能想要提供了使用工具提示的文本说明。  
  
 此外可以通过设置禁用的单元格级别工具提示显示<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>属性设置为`false`。  
  
### <a name="to-add-a-tooltip-to-a-cell"></a>若要向单元格添加工具提示  
  
-   设置 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> 属性。  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
  
-   此示例需要：  
  
-   一个<xref:System.Windows.Forms.DataGridView>名为控件`dataGridView1`，其中包含一个名为列`Rating`显示字符串值的一到四个星号 ("*") 符号。 <xref:System.Windows.Forms.DataGridView.CellFormatting>控件的事件必须与在示例中所示的事件处理程序方法关联。  
  
-   对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="robust-programming"></a>可靠编程  
 当绑定<xref:System.Windows.Forms.DataGridView>到外部数据源控件或通过实现虚拟模式下提供您自己的数据源，可能会遇到性能问题。 若要使用的大量数据时，请避免对性能产生负面影响，请处理<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>事件而不是设置<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>的多个单元格的属性。 当处理此情况下，获取单元格的值<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>属性引发事件，并返回的值<xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType>属性设置为指定在事件处理程序。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [使用 Windows 窗体 DataGridView 控件中的单元格、行和列编程](programming-with-cells-rows-and-columns-in-the-datagrid.md)
