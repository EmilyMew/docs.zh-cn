---
title: DataGrid 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- DataGrid
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- columns [Windows Forms], DataGrid control
- data sources [Windows Forms], binding to DataGrid control
- tables [Windows Forms], binding to DataGrid control
- DataGrid control [Windows Forms], data binding
- DataGrid control [Windows Forms], about DataGrid control
- parent tables in DataGrid control
- tables [Windows Forms], displaying in DataGrid control
- data grids [Windows Forms], about data grids
- multiple tables in DataGrid control
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- parent table navigation in DataGrid
- child tables [Windows Forms], dataGrid control
ms.assetid: 85604bce-bc03-49d9-9030-dda8896c44b1
ms.openlocfilehash: 33f6e5f7929c5a4231c0779964db177f45af6743
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055204"
---
# <a name="datagrid-control-overview-windows-forms"></a>DataGrid 控件概述（Windows 窗体）
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控件取代了 <xref:System.Windows.Forms.DataGrid> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.DataGrid> 控件以实现向后兼容并供将来使用。 有关详细信息，请参阅 [Windows 窗体 DataGridView 控件与 DataGrid 控件之间的区别](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 Windows 窗体 <xref:System.Windows.Forms.DataGrid> 控件将数据显示在一些列行和列中。 最简单的情况是网格绑定到不包含任何关系的单个表的数据源。 在这种情况下，数据显示在简单的行和列中，如在电子表格中一样。 有关将数据绑定到其他控件的详细信息，请参阅[数据绑定和 Windows 窗体](../data-binding-and-windows-forms.md)。  
  
 如果 <xref:System.Windows.Forms.DataGrid> 绑定到多个相关表的数据，并在网格上启用了导航功能，则网格中的每行都将显示扩展器。 借助扩展器，用户可以从父表移到子表。 单击节点将显示子表，单击后退按钮将显示原始父表。 网格以这种方式显示表与表之间的层次结构关系。  
  
 以下屏幕截图显示绑定到多个表的数据的 DataGrid。  
  
 ![绑定到多个表的数据的 DataGrid](./media/vbcontrol1.gif "vbControl1")  
绑定到多个表的数据的 DataGrid  
  
 <xref:System.Windows.Forms.DataGrid> 可提供数据集、相关表之间导航以及丰富格式设置和编辑功能的用户界面。  
  
 显示和操作数据是单独的函数：该控件处理用户界面，而由 Windows 窗体数据绑定体系结构和处理数据更新[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]数据提供程序。 因此绑定到同一数据源的多个控件将保持同步。  
  
> [!NOTE]
>  如果你熟悉 Visual Basic 6.0 中的 DataGrid 控件，就会发现 Windows 窗体 <xref:System.Windows.Forms.DataGrid> 控件中的一些重要差异。  
  
 当网格绑定到 <xref:System.Data.DataSet> 时，会自动创建列和行，同时对其格式进行设置并填充数据。 有关更多信息，请参见 [Data Binding and Windows Forms](../data-binding-and-windows-forms.md)。 生成 <xref:System.Windows.Forms.DataGrid> 控件后，可根据需要对列和行进行添加、删除、重新排列以及设置格式。  
  
## <a name="binding-data-to-the-control"></a>将数据绑定到控件  
 若要使 <xref:System.Windows.Forms.DataGrid> 控件起作用，应在设计时使用 <xref:System.Windows.Forms.DataGrid.DataSource%2A> 和 <xref:System.Windows.Forms.DataGrid.DataMember%2A> 属性或在运行时使用 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> 方法将该控件绑定到数据源。 通过这种绑定，可以使 <xref:System.Windows.Forms.DataGrid> 指向一个实例化的数据源对象，如 <xref:System.Data.DataSet> 或 <xref:System.Data.DataTable>。 <xref:System.Windows.Forms.DataGrid> 控件显示对数据执行操作所产生的结果。 大多数特定于数据的操作并不是通过 <xref:System.Windows.Forms.DataGrid> 执行的，而是通过数据源执行。  
  
 如果绑定数据集中的数据通过任何机制进行了更新，那么 <xref:System.Windows.Forms.DataGrid> 控件会反映这些变化。 如果数据网格及其表样式和列样式`ReadOnly`属性设置为`false`，可以通过更新数据集中<xref:System.Windows.Forms.DataGrid>控件。  
  
 <xref:System.Windows.Forms.DataGrid> 一次只能显示一张表。 如果在表与表之间定义了父-子关系，则用户可以在相关表之间移动以选择要显示在 <xref:System.Windows.Forms.DataGrid> 控件中的表。 有关绑定信息<xref:System.Windows.Forms.DataGrid>控制对[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]数据源在设计时或运行的时，请参阅[如何：将 Windows 窗体 DataGrid 控件绑定到数据源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)。  
  
 <xref:System.Windows.Forms.DataGrid> 的有效数据源包括：  
  
-   <xref:System.Data.DataTable> class  
  
-   <xref:System.Data.DataView> class  
  
-   <xref:System.Data.DataSet> class  
  
-   <xref:System.Data.DataViewManager> class  
  
 如果源是一个数据集，那么该数据集可能是窗体中的某个对象或由 XML Web 服务传递到该窗体的某个对象。 可以绑定到类型化数据集，也可以绑定到非类型化数据集。  
  
 如果结构中的对象（例如数组中的元素）公开公共属性，则还可以将 <xref:System.Windows.Forms.DataGrid> 控件绑定到其他结构。 网格将显示结构中该元素的所有公共属性。 例如，如果将 <xref:System.Windows.Forms.DataGrid> 控件绑定到客户对象数组，那么网格将显示这些客户对象的所有公共属性。 某些情况下，这意味着尽管可以绑定到结构，但最终绑定的结构可能不具有实际应用程序。 例如，你可以绑定到整数数组，但由于 `Integer` 数据类型不支持公共属性，因此该网格不会显示任何数据。  
  
 如果其元素公开公共属性，则可以绑定到以下结构：  
  
-   实现 <xref:System.Collections.IList> 接口的任意组件。 这包括单维数组。  
  
-   实现 <xref:System.ComponentModel.IListSource> 接口的任意组件。  
  
-   实现 <xref:System.ComponentModel.IBindingList> 接口的任意组件。  
  
 有关可能数据源的详细信息，请参阅 [Windows 窗体支持的数据源](../data-sources-supported-by-windows-forms.md)。  
  
## <a name="grid-display"></a>网格显示  
 <xref:System.Windows.Forms.DataGrid> 控件的一个常见用途是显示数据集中的单个数据表。 但是，该控件还可以用于显示多个表，包括相关表。 网格的显示可根据数据源自动调整。 下表显示各种配置显示的内容。  
  
|数据集内容|显示内容|  
|--------------------------|-----------------------|  
|单个表。|表显示在网格中。|  
|多个表。|网格可以显示树视图，用户可以通过浏览树视图找到希望显示的表。|  
|多个相关表。|网格可以显示树视图以便选择表格，你也可指定网格显示父表。 通过父表中的记录，用户可导航到相关的子行。|  
  
> [!NOTE]
> 使用 <xref:System.Data.DataRelation> 使数据集中的表相关。 另请参阅[创建数据集之间的关系](/visualstudio/data-tools/relationships-in-datasets)。
  
 当 <xref:System.Windows.Forms.DataGrid> 控件显示表并且 <xref:System.Windows.Forms.DataGrid.AllowSorting%2A> 属性设置为 `true` 时，可通过单击列标题对数据重新排序。 用户还可以添加行和编辑单元格。  
  
 通过使用父/子导航结构，向用户显示一组表之间的关系。 父表是最高级别的数据，子表是派生自父表中各个列表的数据表。 扩展器显示在包含子表的每个父行中。 单击扩展器将生成指向子表的类似 Web 链接的列表。 当用户选择某个链接时，将显示子表。 单击“显示/隐藏父行”图标（![显示/隐藏父行图标](./media/vbicon.gif "vbIcon")）会隐藏父表的相关信息，如果用户之前已经执行过隐藏操作，则会重新显示此信息。 用户可以单击后退按钮，返回到之前查看的表。  
  
## <a name="columns-and-rows"></a>列和行  
 <xref:System.Windows.Forms.DataGrid> 由 <xref:System.Windows.Forms.DataGrid> 控件的 <xref:System.Windows.Forms.DataGrid.TableStyles%2A> 属性中包含的 <xref:System.Windows.Forms.DataGridTableStyle> 对象集合组成。 表样式可能具有 <xref:System.Windows.Forms.DataGridTableStyle> 的 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> 属性中包含的 <xref:System.Windows.Forms.DataGridColumnStyle> 对象集合。 您可以编辑<xref:System.Windows.Forms.DataGrid.TableStyles%2A>并<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>属性使用通过访问的集合编辑器**属性**窗口。  
  
 任何与 <xref:System.Windows.Forms.DataGrid> 控件关的联 <xref:System.Windows.Forms.DataGridTableStyle> 都可通过 <xref:System.Windows.Forms.GridTableStylesCollection> 进行访问。 可利用 <xref:System.Windows.Forms.DataGridTableStyle> 集合编辑器在设计器中编辑 <xref:System.Windows.Forms.GridTableStylesCollection>，或以编程方式通过 <xref:System.Windows.Forms.DataGrid> 控件的 <xref:System.Windows.Forms.DataGrid.TableStyles%2A> 属性进行编辑。  
  
 ![DataGrid 控件中包含的对象](./media/vbcolumns1.gif "vbColumns1")  
下图显示 DataGrid 控件中包含的对象。  
  
 通过将表样式和列样式的 `MappingName` 属性设置为相应的 <xref:System.Data.DataTable.TableName%2A> 和 <xref:System.Data.DataColumn.ColumnName%2A> 属性，使它们与 <xref:System.Data.DataTable> 对象和 <xref:System.Data.DataColumn> 对象保持同步。 当将没有列样式的 <xref:System.Windows.Forms.DataGridTableStyle> 添加至绑定到有效数据源的 <xref:System.Windows.Forms.DataGrid> 控件，并且将该表样式的 <xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A> 属性设置为有效的 <xref:System.Data.DataTable.TableName%2A> 属性时，会针对该表样式创建 <xref:System.Windows.Forms.DataGridColumnStyle> 对象集合。 对于在 <xref:System.Data.DataTable> 的 <xref:System.Data.DataTable.Columns%2A> 集合中发现的每个 <xref:System.Data.DataColumn>，都会将相应的 <xref:System.Windows.Forms.DataGridColumnStyle> 添加至 <xref:System.Windows.Forms.GridColumnStylesCollection>。 <xref:System.Windows.Forms.GridColumnStylesCollection> 通过访问<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>属性的<xref:System.Windows.Forms.DataGridTableStyle>。 通过对 <xref:System.Windows.Forms.GridColumnStylesCollection> 使用 <xref:System.Windows.Forms.GridColumnStylesCollection.Add%2A> 或 <xref:System.Windows.Forms.GridColumnStylesCollection.Remove%2A> 方法在网格中添加或删除列。 有关详细信息，请参阅[如何：添加表和列到 Windows 窗体 DataGrid 控件](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)和[如何：删除或隐藏列在 Windows 窗体 DataGrid 控件](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)。  
  
 列类型的集合可扩展具有丰富格式设置和编辑功能的 <xref:System.Windows.Forms.DataGridColumnStyle> 类。 所有列类型都继承自 <xref:System.Windows.Forms.DataGridColumnStyle> 基类。 创建的类取决于 <xref:System.Web.UI.WebControls.DataGridColumn> 基于的 <xref:System.Data.DataColumn> 的 <xref:System.Data.DataColumn.DataType%2A> 属性。 例如，<xref:System.Data.DataColumn.DataType%2A> 属性设置为 <xref:System.Boolean> 的 <xref:System.Data.DataColumn> 将与 <xref:System.Windows.Forms.DataGridBoolColumn> 关联。 下表描述了每种列类型。  
  
|列名称|描述|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.DataGridTextBoxColumn>|接受并显示数据为格式化或非格式化的字符串。 编辑功能与在简单的 <xref:System.Windows.Forms.TextBox> 中编辑数据相同。 继承自 <xref:System.Windows.Forms.DataGridColumnStyle>。|  
|<xref:System.Windows.Forms.DataGridBoolColumn>|接受并显示 `true`、`false` 和 null 值。 继承自 <xref:System.Windows.Forms.DataGridColumnStyle>。|  
  
 双击列的右边缘可调整列大小，以显示其完整的标题和最宽的条目。  
  
## <a name="table-styles-and-column-styles"></a>表样式和列样式  
 建立了 <xref:System.Windows.Forms.DataGrid> 控件的默认格式后，便可以自定义在数据网格中显示某些表时将使用的颜色。  
  
 这可通过创建 <xref:System.Windows.Forms.DataGridTableStyle> 类中的实例得以实现。 表样式指定了与 <xref:System.Windows.Forms.DataGrid> 控件本身默认格式设置不同的特定表的格式设置。 每张表每次只能定义一种表样式。  
  
 有时，你会希望特定数据表中的特定列不同于表中的其他列。 你可以通过使用 <xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A> 属性创建一组自定义的列样式。  
  
 列样式与数据集中列相关，同样，表样式也与数据表相关。 与每张表每次只能定义一种表样式相同，在特定的表样式中每列也只能定义一种列样式。 此关系在列的 <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> 属性中定义。  
  
 如果您已经创建表样式，而无需向其中添加列样式，Visual Studio 将在运行时创建窗体和网格时添加默认列样式。 但是，如果已经创建了表样式，并向其添加任何列样式，Visual Studio 将不创建任何列样式。 此外，还需要定义列样式，并向它们分配映射名称以便在网格中显示你希望显示的列。  
  
 由于数据网格中包含的列是通过向它们分配列样式指定的，而尚未向列分配列样式，因此可包含网格中未显示的数据集中的数据列。 然而，由于数据列包含在数据集中，因此可采用编程方式来编辑未显示的数据。  
  
> [!NOTE]
>  一般情况下，应先创建列样式并将其添加到列样式集合，然后再向表样式集合添加表样式。 当将空表样式添加到集合时，会自动生成列样式。 因此，如果尝试向列样式集合添加具有重复 <xref:System.Windows.Forms.DataGridColumnStyle.MappingName%2A> 值的新列样式，则将引发异常。  
>   
>  有时，你可能只希望微调众多列中的某一列，例如，数据集包含 50 列，而你只需要其中的 49 列。 在这种情况下，相对简单的办法是导入所有 50 列，然后以编程方式删除其中的一列，而不是以编程方式添加 49 个单独的列。  
  
## <a name="formatting"></a>格式化  
 可应用于 <xref:System.Windows.Forms.DataGrid> 控件的格式设置包括边框样式、网格线样式、字体、标题属性、数据对齐以及交替行之间的背景颜色。 有关详细信息，请参阅[如何：设置 Windows 窗体 DataGrid 控件的格式](how-to-format-the-windows-forms-datagrid-control.md)。  
  
## <a name="events"></a>事件  
 除了常见的控件事件（如 <xref:System.Windows.Forms.Control.MouseDown>、<xref:System.Windows.Forms.Control.Enter> 和 <xref:System.Windows.Forms.DataGrid.Scroll>），<xref:System.Windows.Forms.DataGrid> 控件还支持在网格内进行编辑和导航。 <xref:System.Windows.Forms.DataGrid.CurrentCell%2A> 属性用于确定选择哪个单元格。 当用户导航到新的单元格时，将引发 <xref:System.Windows.Forms.DataGrid.CurrentCellChanged> 事件。 当用户通过父/子关系导航到新表时，将引发 <xref:System.Windows.Forms.DataGrid.Navigate> 事件。 当用户单击后退按钮和查看子表时，将引发 <xref:System.Windows.Forms.DataGrid.BackButtonClick> 事件；当单击“显示/隐藏父行”图标时，将引发 <xref:System.Windows.Forms.DataGrid.ShowParentDetailsButtonClick> 事件。  
  
## <a name="see-also"></a>请参阅
- [DataGrid 控件](datagrid-control-windows-forms.md)
- [如何：将 Windows 窗体 DataGrid 控件绑定到数据源](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [如何：向 Windows 窗体 DataGrid 控件添加表和列](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [如何：在 Windows 窗体 DataGrid 控件中删除或隐藏列](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [如何：设置 Windows 窗体 DataGrid 控件的格式](how-to-format-the-windows-forms-datagrid-control.md)
