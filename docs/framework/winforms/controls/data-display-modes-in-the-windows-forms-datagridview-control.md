---
title: Windows 窗体 DataGridView 控件中的数据显示模式
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: 673780909f6d66168548893e99d79bbfec70a0e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079690"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Windows 窗体 DataGridView 控件中的数据显示模式
<xref:System.Windows.Forms.DataGridView>控件可以显示三种不同模式中的数据： 绑定、 未绑定，和虚拟。 选择最合适的模式基于你的要求。  
  
## <a name="unbound"></a>未绑定  
 取消绑定的模式适合用于显示的以编程方式管理的数据量相对较少。 不附加<xref:System.Windows.Forms.DataGridView>直接与数据源如下所示绑定模式的控件。 相反，您必须亲自填充该控件，通常使用<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>方法。  
  
 未绑定的模式可以是静态的只读数据，或当您想要与外部数据存储区提供你自己的代码进行交互时尤其有用。 当你想在用户与外部数据源进行交互时，但是，将通常使用绑定的模式。  
  
 使用一个只读的示例，未绑定<xref:System.Windows.Forms.DataGridView>，请参阅[如何：创建未绑定的 Windows 窗体 DataGridView 控件](how-to-create-an-unbound-windows-forms-datagridview-control.md)。  
  
## <a name="bound"></a>绑定  
 绑定的模式是适用于管理数据使用与数据存储区的自动交互。 可以将附加<xref:System.Windows.Forms.DataGridView>直接向通过设置其数据源控件<xref:System.Windows.Forms.DataGridView.DataSource%2A>属性。 数据绑定控件时，推送和拉取而无需显式管理您的数据行。 当<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>属性是`true`，数据源中的每一列将导致控件中创建相对应的列。 如果想要创建自己的列，可以将此属性设置为`false`，并使用<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>要绑定的每个列时将其配置属性。 当你想要使用的类型与默认情况下生成的类型的列类型时，这很有用。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)。  
  
 有关使用绑定的示例<xref:System.Windows.Forms.DataGridView>控件，请参阅[演练：验证 Windows 中的数据窗体 DataGridView 控件](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)。  
  
 您还可以添加到未绑定的列<xref:System.Windows.Forms.DataGridView>绑定模式中的控件。 当你想要显示的按钮或链接，可让用户执行操作的特定行的列时，这很有用。 也很有用，与计算从绑定列的值显示列。 您可以填充的单元格值的处理程序中的计算列的<xref:System.Windows.Forms.DataGridView.CellFormatting>事件。 如果使用的<xref:System.Data.DataSet>或<xref:System.Data.DataTable>作为数据源，但是，你可能想要使用<xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>属性改为创建计算的列。 在这种情况下，<xref:System.Windows.Forms.DataGridView>控制会将计算的列就像任何其他列中的数据源一样。  
  
 不支持通过在绑定模式下的未绑定列进行排序。 如果在包含用户可编辑值的绑定模式下创建未绑定的列，则必须实现虚拟模式下，该控件绑定的列进行排序时保留这些值。  
  
## <a name="virtual"></a>虚拟  
 随着虚拟模式下，您可以实现自己的数据管理操作。 这是在绑定模式下维护未绑定列的值，该控件绑定列进行排序时所必需的。 但是，虚拟模式的主要用途是与大量的数据进行交互时优化性能。  
  
 附加<xref:System.Windows.Forms.DataGridView>你管理的缓存控制和代码控件时推送和拉取数据行。 若要保留的内存占用量小，缓存应在大小上类似于当前显示的行数。 当用户滚动到视图的新行时，代码请求缓存中的新数据，并可选择从内存中将旧数据。  
  
 在实现虚拟模式时，需要跟踪新行回滚新行添加到需要在数据模型中时。 此功能的具体实现将取决于数据模型中; 的事务语义和实现数据模型是否提交作用域是在单元格或行级别。  
  
 有关虚拟模式的详细信息，请参阅[Windows 窗体 DataGridView 控件中的虚拟模式](virtual-mode-in-the-windows-forms-datagridview-control.md)。 有关演示如何使用虚拟模式下的事件的示例，请参阅[演练：在 Windows 中实现虚拟模式窗体 DataGridView 控件](implementing-virtual-mode-wf-datagridview-control.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [在 Windows 窗体 DataGridView 控件中显示数据](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)
- [演练：创建未绑定的 Windows 窗体 DataGridView 控件](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [如何：将数据绑定到 Windows 窗体 DataGridView 控件](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的虚拟模式](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [演练：在 Windows 窗体 DataGridView 控件中实现虚拟模式](implementing-virtual-mode-wf-datagridview-control.md)
