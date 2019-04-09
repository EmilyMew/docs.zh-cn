---
title: Windows 窗体 DataGridView 控件和 DataGrid 控件之间的区别
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 6802ef375d8d15826725e68f5065317192523178
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095667"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows 窗体 DataGridView 控件和 DataGrid 控件之间的区别
<xref:System.Windows.Forms.DataGridView>控件是新控件，用于替换<xref:System.Windows.Forms.DataGrid>控件。 <xref:System.Windows.Forms.DataGridView>控件提供了许多的基本和高级功能，中缺少<xref:System.Windows.Forms.DataGrid>控件。 此外的体系结构<xref:System.Windows.Forms.DataGridView>控件，可以更轻松地扩展和自定义比<xref:System.Windows.Forms.DataGrid>控件。  
  
 下表描述中提供的主要功能的一些<xref:System.Windows.Forms.DataGridView>控件中缺少<xref:System.Windows.Forms.DataGrid>控件。  
  
|DataGridView 控件功能|描述|  
|----------------------------------|-----------------|  
|多个列类型|<xref:System.Windows.Forms.DataGridView>控件提供了更多的内置列类型，而不<xref:System.Windows.Forms.DataGrid>控件。 这些列类型满足最常见的方案，但也更轻松地扩展或替换中的列类型比<xref:System.Windows.Forms.DataGrid>控件。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)。|  
|通过多种方式来显示数据|<xref:System.Windows.Forms.DataGrid>控件仅限于从外部数据源显示数据。 <xref:System.Windows.Forms.DataGridView>控件，但是，可以显示未绑定的数据一起存储在控件、 数据绑定的数据源或绑定和未绑定的数据。 您还可以实现中的虚拟模式<xref:System.Windows.Forms.DataGridView>控件提供自定义数据管理。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的数据显示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)。|  
|通过多种方式自定义数据显示|<xref:System.Windows.Forms.DataGridView>控件提供了很多属性和事件，使您可以指定如何格式化和显示数据。 例如，您可以更改的单元格、 行和列，具体取决于它们所包含的数据外观或一种数据类型的数据替换为等效的另一种类型的数据。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的数据格式设置](data-formatting-in-the-windows-forms-datagridview-control.md)。|  
|更改单元格、 行、 列和标头的外观和行为的多个选项|<xref:System.Windows.Forms.DataGridView>控件使您可以使用以下几个方面的各网格组件。 例如，可以冻结行和列，以防止其滚动，则为隐藏行、 列和标头;更改调整行、 列和标头大小; 方法更改用户进行选择; 的方式并为每个单元格、 行和列提供工具提示和快捷方式菜单。|  
  
 <xref:System.Windows.Forms.DataGrid>向后兼容性和特殊需要保留控件。 对于几乎所有，应使用<xref:System.Windows.Forms.DataGridView>控件。 现已推出的唯一功能<xref:System.Windows.Forms.DataGrid>中不可用的控件<xref:System.Windows.Forms.DataGridView>控件是在单个控件中的两个相关表中的信息的层次结构显示。 必须使用两个<xref:System.Windows.Forms.DataGridView>控件显示的主/从关系中的两个表中的信息。  
  
## <a name="upgrading-to-the-datagridview-control"></a>升级到 DataGridView 控件  
 如果你的现有应用程序使用<xref:System.Windows.Forms.DataGrid>控件在简单数据绑定方案中而无需自定义项，只需可以使用新的控件替换的旧控件。 这两个控件使用标准 Windows 窗体数据绑定体系结构，因此<xref:System.Windows.Forms.DataGridView>控件将显示为无需其他配置的绑定的数据。 可能需要考虑利用数据绑定的改进，但是，通过将绑定到数据<xref:System.Windows.Forms.BindingSource>组件，然后可以绑定到<xref:System.Windows.Forms.DataGridView>控件。 有关详细信息，请参阅[BindingSource 组件](bindingsource-component.md)。  
  
 因为<xref:System.Windows.Forms.DataGridView>控件具有一个全新体系结构，没有简单的转换路径，您可以使用<xref:System.Windows.Forms.DataGrid>自定义项与<xref:System.Windows.Forms.DataGridView>控件。 许多<xref:System.Windows.Forms.DataGrid>自定义项都是使用不必要<xref:System.Windows.Forms.DataGridView>控制，但是，由于新控件中提供的内置功能。 如果已创建的自定义列类型<xref:System.Windows.Forms.DataGrid>你想要用于控件<xref:System.Windows.Forms.DataGridView>控件，将具有用于实现它们再次使用新的体系结构。 有关详细信息，请参阅[自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView 控件](datagridview-control-windows-forms.md)
- [DataGrid 控件](datagrid-control-windows-forms.md)
- [BindingSource 组件](bindingsource-component.md)
- [Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的数据显示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的数据格式设置](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的大小调整选项](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的列排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的选择模式](selection-modes-in-the-windows-forms-datagridview-control.md)
- [自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)
