---
title: Windows 窗体 DataGridView 控件中的选择模式
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: 79e13e65938252015e43b59a962d40f20963a5df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097273"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows 窗体 DataGridView 控件中的选择模式
有时您希望应用程序来执行基于用户所做选择中操作<xref:System.Windows.Forms.DataGridView>控件。 具体取决于操作，你可能想要限制可使用所选内容的类型。 例如，假设你的应用程序可以打印当前所选记录的报表。 在这种情况下，可能想要配置<xref:System.Windows.Forms.DataGridView>控件，以便单击的任意位置的行始终选择整行，并且可以选择一次只有一个行。  
  
 您可以指定允许通过设置所选内容<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>属性设置为下列任一<xref:System.Windows.Forms.DataGridViewSelectionMode>枚举值。  
  
|DataGridViewSelectionMode value|描述|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|单击一个单元格选择它。 行和列标题不能用于所选内容。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|单击一个单元格选择它。 单击列标题可以选择整个列。 不能用于列标题排序。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|单击一个单元格或列标题选择整个列。 不能用于列标题排序。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|单击单元格或行标题可以选择整个行。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|默认选择模式。 单击一个单元格选择它。 单击行标题可以选择整行。|  
  
> [!NOTE]
>  更改选择模式，在运行时自动清除当前所选内容。  
  
 默认情况下，用户可以选择多个行、 列或单元格通过拖动鼠标，按住 CTRL 或 SHIFT 的同时选择要扩展或修改所选内容，或单击要在控件中选择所有单元格的左上角的标题单元格。 若要防止此行为，请设置<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>属性设置为`false`。  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>和<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>模式允许用户通过选择它们并按 DELETE 键删除行。 仅当当前单元格不处于编辑模式时，用户可以删除行<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A>属性设置为`true`，并且基础数据源支持面向用户的行删除。 请注意这些设置不会阻止以编程方式行删除。  
  
## <a name="programmatic-selection"></a>以编程方式选择  
 当前的选择模式将限制编程所选内容，以及用户选择的行为。 您可以通过设置以编程方式更改当前所选内容`Selected`属性的任何单元格、 行或列中存在<xref:System.Windows.Forms.DataGridView>控件。 此外可以通过在控件中选择所有单元格<xref:System.Windows.Forms.DataGridView.SelectAll%2A>方法，具体取决于选择模式。 若要清除选择，请使用<xref:System.Windows.Forms.DataGridView.ClearSelection%2A>方法。  
  
 如果<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>属性设置为`true`，可以添加<xref:System.Windows.Forms.DataGridView>到元素或从中选择删除通过更改`Selected`元素的属性。 否则，设置`Selected`属性设置为`true`的一个元素会自动删除所选内容的其他元素。  
  
 请注意，更改的值<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>属性不会更改当前所选内容。  
  
 可以检索当前选定的单元格、 行或列到列的集合<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>， <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>，并<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>的属性<xref:System.Windows.Forms.DataGridView>控件。 选择控件中的每个单元格时，访问这些属性是效率低下。 若要在这种情况下避免对性能产生负面影响，请使用<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>方法第一个。 此外，访问这些集合来确定所选单元格的数目，行或列可以是效率低下。 相反，应使用<xref:System.Windows.Forms.DataGridView.GetCellCount%2A>， <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>，或<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>方法，传入<xref:System.Windows.Forms.DataGridViewElementStates.Selected>值。  
  
> [!TIP]
>  演示如何以编程方式将所选单元格的示例代码可在<xref:System.Windows.Forms.DataGridView>类概述。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Windows 窗体 DataGridView 控件的选项和剪贴板使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [如何：设置 Windows 窗体 DataGridView 控件的选择模式](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
