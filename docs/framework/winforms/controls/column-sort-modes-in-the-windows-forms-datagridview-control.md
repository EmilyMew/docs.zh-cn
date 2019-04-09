---
title: Windows 窗体 DataGridView 控件中的列排序模式
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: b8f6048946d367dd79b1ce0d23d84446ffdb1115
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106661"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows 窗体 DataGridView 控件中的列排序模式
<xref:System.Windows.Forms.DataGridView> 列具有三个排序模式。 通过指定每个列的排序模式<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>属性的列，可以将设置为以下值之一的<xref:System.Windows.Forms.DataGridViewColumnSortMode>枚举值。  
  
|`DataGridViewColumnSortMode` 值|描述|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|默认值对文本中的列。 除非列标头用于进行选择，单击列标题会自动进行排序<xref:System.Windows.Forms.DataGridView>按此列，并显示标志符号，它指示排序顺序。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|默认值为非 – 文本中的列的。 可以对此列排序以编程方式;但是，它不是进行排序，因此排序标志符号不保留任何空间。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|可以对此列排序，以编程方式和排序标志符号保留空间。|  
  
 你可能想要更改默认为列的排序模式<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>包含有意义的方式有序的值。 例如，如果您有一个数据库列包含表示项状态的数字，你可以通过将图像列绑定到的数据库列将这些数字显示为对应的图标中。 然后，可以更改数字的单元格的值中的处理程序的映像显示值<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>事件。 在这种情况下，设置<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>属性设置为<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>允许用户对列进行排序。 自动排序将让你的用户具有相同的状态，即使的数字相对应的状态不具有自然序列的项进行分组。 复选框列是另一个示例，其中自动排序，可用于对相同状态的项进行分组。  
  
 您可以进行排序<xref:System.Windows.Forms.DataGridView>以编程方式或在多个列，而不考虑任何列中的值<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>设置。 您想要提供您自己的用户界面 (UI) 进行排序时或当您想要实现自定义排序，编程排序非常有用。 提供你自己的排序用户界面非常有用，例如，当您设置<xref:System.Windows.Forms.DataGridView>选择模式以启用列标题选择。 在这种情况下，虽然不能用于列标题排序，但仍想要显示相应的排序标志符号，因此，你将设置的标头<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>属性设置为<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>。  
  
 列将设置为以编程方式排序模式未自动显示排序标志符号。 对于这些列中，您必须自己显示标志符号通过设置<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>属性。 这是必需的如果想要自定义排序中的灵活性。 例如，如果您对排序<xref:System.Windows.Forms.DataGridView>按多个列，你可能想要显示多个排序标志符号或无排序标志符号。  
  
 尽管您可以以编程方式进行排序<xref:System.Windows.Forms.DataGridView>按任何列中，某些列，如按钮列可能不包含有意义的方式有序的值。 对于这些列，<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>属性设置<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>指示它将永远不会使用以进行排序，因此无需排序标志符号的标头中保留的空间。  
  
 当<xref:System.Windows.Forms.DataGridView>是已排序的您可以确定排序列和排序顺序通过检查的值<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>和<xref:System.Windows.Forms.DataGridView.SortOrder%2A>属性。 自定义排序操作之后，这些值并无意义。 有关自定义排序的详细信息，请参阅本主题后面的自定义排序部分。  
  
 当<xref:System.Windows.Forms.DataGridView>控件包含绑定和未绑定列进行排序，不能自动维护未绑定列中的值。 若要保留这些值，必须实现虚拟模式下通过设置<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性设置为`true`和处理<xref:System.Windows.Forms.DataGridView.CellValueNeeded>和<xref:System.Windows.Forms.DataGridView.CellValuePushed>事件。 有关详细信息，请参阅[如何：Windows 中的实现虚拟模式窗体 DataGridView 控件](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。 不支持通过在绑定模式下的未绑定列进行排序。  
  
## <a name="programmatic-sorting"></a>编程排序  
 您可以进行排序<xref:System.Windows.Forms.DataGridView>以编程方式通过调用其<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。  
  
 `Sort(DataGridViewColumn,ListSortDirection)`的重载<xref:System.Windows.Forms.DataGridView.Sort%2A>方法采用<xref:System.Windows.Forms.DataGridViewColumn>和一个<xref:System.ComponentModel.ListSortDirection>枚举值作为参数。 此重载时，按具有值，可以有意义的方式排序，但不是想为自动分类配置的列进行排序。 当调用此重载并传入的列<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>属性值为<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>，则<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>和<xref:System.Windows.Forms.DataGridView.SortOrder%2A>将自动设置属性和列标题中显示相应的排序标志符号。  
  
> [!NOTE]
>  当<xref:System.Windows.Forms.DataGridView>控件通过设置绑定到外部数据源<xref:System.Windows.Forms.DataGridView.DataSource%2A>属性，`Sort(DataGridViewColumn,ListSortDirection)`方法重载并不适用于未绑定的列。 此外，当<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性是`true`，可以仅为绑定列调用此重载。 若要确定某列是否为数据绑定，请检查<xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>属性值。 不支持对在绑定模式下的未绑定的列进行排序。  
  
## <a name="custom-sorting"></a>自定义排序  
 你可以自定义<xref:System.Windows.Forms.DataGridView>通过使用`Sort(IComparer)`重载<xref:System.Windows.Forms.DataGridView.Sort%2A>方法或通过处理<xref:System.Windows.Forms.DataGridView.SortCompare>事件。  
  
 `Sort(IComparer)`方法重载采用的实现的类实例<xref:System.Collections.IComparer>作为参数的接口。 此重载时，您想要提供自定义排序;例如，当列中的值没有自然排序顺序或当自然排序顺序是不适当。 在这种情况下，不能使用自动排序，但仍可能希望用户通过单击列标题进行排序。 可以在一个处理程序中调用此重载<xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick>事件，如果选择不使用列标题。  
  
> [!NOTE]
>  `Sort(IComparer)`方法重载时才起作用<xref:System.Windows.Forms.DataGridView>控件未绑定到外部数据源并<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性值是`false`。 若要自定义排序的列绑定到外部数据源，必须使用提供的数据源的排序操作。 处于虚拟模式下，必须提供自己为未绑定列的排序操作。  
  
 若要使用`Sort(IComparer)`方法重载中，您必须创建您自己实现的类<xref:System.Collections.IComparer>接口。 此接口要求您的类实现<xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>方法，向其<xref:System.Windows.Forms.DataGridView>将传递<xref:System.Windows.Forms.DataGridViewRow>对象作为输入时`Sort(IComparer)`调用方法重载。 与此，可以计算出正确的行排序中的任何列的值。  
  
 `Sort(IComparer)`方法重载不会设置<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>并<xref:System.Windows.Forms.DataGridView.SortOrder%2A>属性，因此，你必须始终设置<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>属性来显示排序标志符号。  
  
 作为一种替代方法`Sort(IComparer)`方法重载中，您可以通过实现的处理程序的自定义排序<xref:System.Windows.Forms.DataGridView.SortCompare>事件。 当用户单击列配置为自动排序，或当您调用的标头时发生此事件`Sort(DataGridViewColumn,ListSortDirection)`重载<xref:System.Windows.Forms.DataGridView.Sort%2A>方法。 控件，使您能够计算它们的正确顺序中的行的每个对时发生该事件。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare>事件不会发生时<xref:System.Windows.Forms.DataGridView.DataSource%2A>属性设置时，或者当<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性值是`true`。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [在 Windows 窗体 DataGridView 控件中对数据进行排序](sorting-data-in-the-windows-forms-datagridview-control.md)
- [如何：设置 Windows 窗体 DataGridView 控件中列的排序模式](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [如何：在 Windows 窗体 DataGridView 控件中自定义排序](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
