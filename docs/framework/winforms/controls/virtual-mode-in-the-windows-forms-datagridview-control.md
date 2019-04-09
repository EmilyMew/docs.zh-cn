---
title: Windows 窗体 DataGridView 控件中的虚拟模式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: f284835578221ad1fe859f260e37bb829cd64b2d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124717"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Windows 窗体 DataGridView 控件中的虚拟模式
虚拟模式下，你可以管理之间的交互<xref:System.Windows.Forms.DataGridView>控件和自定义数据缓存。 若要实现虚拟模式下，设置<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性设置为`true`并处理一个或多个本主题中所述的事件。 通常会处理至少`CellValueNeeded`事件，它使数据缓存中的值查找的控件。  
  
## <a name="bound-mode-and-virtual-mode"></a>绑定的模式和虚拟模式  
 仅在需要以补充或替代绑定的模式时，才需要虚拟模式。 绑定模式下，在您设置<xref:System.Windows.Forms.DataGridView.DataSource%2A>属性和控件自动从指定的源加载数据，并提交用户更改返回到它。 您可以控制显示哪些绑定列和数据源本身通常会处理操作，如排序。  
  
## <a name="supplementing-bound-mode"></a>补充绑定的模式  
 你可以通过显示未绑定的列绑定的列以及补充绑定的模式。 这有时称为"混合的模式"，并可用于显示某些操作，如计算出的值或用户界面 (UI) 控件。  
  
 由于未绑定的列是外部数据源，它们将忽略数据源的排序操作。 因此，如果启用排序在混合模式下，您必须管理在本地缓存中的未绑定的数据并实现虚拟模式以使<xref:System.Windows.Forms.DataGridView>控件与之进行交互。  
  
 有关使用虚拟模式下维护未绑定列中的值的详细信息，请参阅中的示例<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType>属性和<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>类参考主题。  
  
## <a name="replacing-bound-mode"></a>替换绑定的模式  
 如果绑定的模式不满足性能需求，你可以管理通过虚拟模式事件处理程序的自定义缓存中的所有数据。 例如，可以使用的虚拟模式实现在实时数据加载机制，以仅检索数量的数据从联网的数据库必须以获得最佳性能。 此方案中使用大量的数据通过慢速网络连接或具有有限的数量的 RAM 或存储空间的客户端计算机时特别有用。  
  
 有关在实时方案中使用的虚拟模式的详细信息，请参阅[实时数据加载 Windows 窗体 DataGridView 控件中实现虚拟模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)。  
  
## <a name="virtual-mode-events"></a>虚拟模式事件  
 如果你的数据是只读的`CellValueNeeded`事件可能是您将需要处理的唯一事件。 其他虚拟模式事件使您可以启用特定功能，例如用户编辑、 添加行和删除和行级事务。  
  
 一些标准<xref:System.Windows.Forms.DataGridView>事件 （如用户添加或删除行，或单元格时的值时发生的事件进行编辑、 分析、 验证，或格式） 均处于虚拟模式非常有用。 此外可以处理事件，可维护通常不存储在绑定的数据源，例如单元格工具提示文本、 单元格和行错误文本、 单元格和行的快捷菜单数据和行高度数据中的值。  
  
 有关实现虚拟模式来管理具有行级别的提交作用域的读/写数据的详细信息，请参阅[演练：在 Windows 中实现虚拟模式窗体 DataGridView 控件](implementing-virtual-mode-wf-datagridview-control.md)。  
  
 实现虚拟模式的单元格级提交作用域的示例，请参阅<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性参考主题。  
  
 仅将发生以下事件时<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性设置为`true`。  
  
|Event|描述|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|该控件用于从显示的数据缓存中检索的单元值。 仅对未绑定的列中的单元格时发生此事件。|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|该控件用于将用户输入的单元格提交到数据缓存。 仅对未绑定的列中的单元格时发生此事件。<br /><br /> 调用<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>方法时更改缓存的值之外的<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件处理程序以确保在控件中显示的当前值并应用当前有效的任何自动调整大小模式。|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|该控件用于指示要使用的数据缓存中的新行。|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|该控件用于确定行是否有任何未提交的更改。|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|该控件用于指示行应恢复为其缓存的值。|  
  
 以下事件可在虚拟模式下，但可以使用而不考虑<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性设置。  
  
|事件|描述|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|该控件用于指示当行被删除或添加，从而相应地更新数据缓存。|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|用于通过格式单元格的值的控件用于显示和分析和验证用户输入。|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|该控件用于检索单元格工具提示文本时<xref:System.Windows.Forms.DataGridView.DataSource%2A>属性设置或<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性是`true`。<br /><br /> 显示单元格工具提示时，才<xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A>属性值是`true`。|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|该控件用于检索单元格或行错误文本时<xref:System.Windows.Forms.DataGridView.DataSource%2A>属性设置或<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性是`true`。<br /><br /> 调用<xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A>方法或<xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A>方法时更改单元格或行错误文本，以确保在控件中显示的当前值。<br /><br /> 显示单元格和行错误标志符号时<xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A>并<xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A>属性的值为`true`。|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|该控件用于检索单元格或行<xref:System.Windows.Forms.ContextMenuStrip>时该控件<xref:System.Windows.Forms.DataGridView.DataSource%2A>属性设置或<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性是`true`。|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|由该控件用于检索或存储的数据缓存中的行的高度信息。 调用<xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A>方法时更改之外的缓存的行高度信息<xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>事件处理程序以确保在控件的显示中使用的当前值。|  
  
## <a name="best-practices-in-virtual-mode"></a>处于虚拟模式下的最佳实践  
 为了有效地使用大量的数据，要实现虚拟模式下，如果您还需要确保与你也会有效地工作<xref:System.Windows.Forms.DataGridView>控件本身。 有关有效地使用的单元格样式、 自动调整大小、 选择以及行共享的详细信息，请参阅[缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Windows 窗体 DataGridView 控件中的性能优化](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [演练：在 Windows 窗体 DataGridView 控件中实现虚拟模式](implementing-virtual-mode-wf-datagridview-control.md)
- [在 Windows 窗体 DataGridView 控件中实现实时数据加载的虚拟模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
