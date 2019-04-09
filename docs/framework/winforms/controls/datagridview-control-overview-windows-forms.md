---
title: DataGridView 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 095c89fd305b1eeb73e2919760abe48e848c6aa0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112874"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView 控件概述（Windows 窗体）
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> 控件取代了 <xref:System.Windows.Forms.DataGrid> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.DataGrid> 控件以实现向后兼容并供将来使用。 有关详细信息，请参阅 [Windows 窗体 DataGridView 控件与 DataGrid 控件之间的区别](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 使用<xref:System.Windows.Forms.DataGridView>控件，可以显示和编辑来自许多不同类型的数据源的表格格式数据。  
  
 数据绑定到<xref:System.Windows.Forms.DataGridView>控件既简单又直观，并在许多情况下它只需设置<xref:System.Windows.Forms.DataGridView.DataSource%2A>属性。 在绑定到数据源包含多个列表或表时，设置<xref:System.Windows.Forms.DataGridView.DataMember%2A>属性设置为一个字符串，指定该表要绑定到的列表。  
  
 <xref:System.Windows.Forms.DataGridView>控件支持标准 Windows 窗体数据绑定模型，因此它可以绑定到以下列表所述的类的实例：  
  
-   任何实现类都<xref:System.Collections.IList>界面，包括一维数组。  
  
-   任何实现类都<xref:System.ComponentModel.IListSource>接口，如<xref:System.Data.DataTable>和<xref:System.Data.DataSet>类。  
  
-   任何实现类都<xref:System.ComponentModel.IBindingList>接口，如<xref:System.ComponentModel.BindingList%601>类。  
  
-   任何实现类都<xref:System.ComponentModel.IBindingListView>接口，如<xref:System.Windows.Forms.BindingSource>类。  
  
 <xref:System.Windows.Forms.DataGridView>控件支持数据绑定到这些接口由返回的对象的公共属性或返回的属性集合<xref:System.ComponentModel.ICustomTypeDescriptor>接口，如果在返回的对象上实现。  
  
 通常情况下，将绑定到<xref:System.Windows.Forms.BindingSource>组件和 bind<xref:System.Windows.Forms.BindingSource>组件到另一个数据源，或使用业务对象填充它。 <xref:System.Windows.Forms.BindingSource>组件是首选的数据源，因为它可以绑定到各种数据源，并且可以自动解决许多数据绑定问题。 有关详细信息，请参阅[BindingSource 组件](bindingsource-component.md)。  
  
 <xref:System.Windows.Forms.DataGridView>控件还可在*未绑定*模式下，不带任何基础数据存储。 有关使用未绑定的代码示例<xref:System.Windows.Forms.DataGridView>控件，请参阅[演练：创建未绑定的 Windows 窗体 DataGridView 控件](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)。  
  
 <xref:System.Windows.Forms.DataGridView>控件是高度可配置且可扩展的并提供许多属性、 方法和事件，以自定义其外观和行为。 当你想在 Windows 窗体应用程序，以显示表格数据时，请考虑使用<xref:System.Windows.Forms.DataGridView>先于其他控件 (例如， <xref:System.Windows.Forms.DataGrid>)。 如果您要显示一个小网格的只读的值，或如果要启用用户无法编辑的表的数百万记录，<xref:System.Windows.Forms.DataGridView>控件将为您提供一个可编程轻松、 高效利用内存的解决方案。  
  
## <a name="in-this-section"></a>本节内容  
 [DataGridView 控件技术摘要](datagridview-control-technology-summary-windows-forms.md)  
 总结了<xref:System.Windows.Forms.DataGridView>控件的概念和相关类的用法。  
  
 [DataGridView 控件体系结构](datagridview-control-architecture-windows-forms.md)  
 介绍的体系结构<xref:System.Windows.Forms.DataGridView>控件，解释了其类型层次结构和继承结构。  
  
 [DataGridView 控件方案](datagridview-control-scenarios-windows-forms.md)  
 介绍在其中的最常见方案<xref:System.Windows.Forms.DataGridView>使用控件。  
  
 [DataGridView 控件代码目录](datagridview-control-code-directory-windows-forms.md)  
 提供了指向各种文档中的代码示例<xref:System.Windows.Forms.DataGridView>任务。 这些示例按任务类型进行分类。  
  
## <a name="related-sections"></a>相关章节  
 [Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)  
 讨论在 Windows 窗体中的列类型<xref:System.Windows.Forms.DataGridView>控件用于显示信息，并允许用户修改或添加信息。  
  
 [在 Windows 窗体 DataGridView 控件中显示数据](displaying-data-in-the-windows-forms-datagridview-control.md)  
 提供一些主题，描述如何手动或从外部数据源向控件填充数据。  
  
 [自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)  
 提供一些主题，介绍自定义绘制 <xref:System.Windows.Forms.DataGridView> 单元格和行，以及创建派生的单元、列和行类型。  
  
 [Windows 窗体 DataGridView 控件中的性能优化](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 提供一些主题，介绍如何在使用大量数据时，有效地使用控件以避免性能问题。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView 控件](datagridview-control-windows-forms.md)
- [Windows 窗体 DataGridView 控件中的默认功能](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的默认键盘和鼠标处理](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
