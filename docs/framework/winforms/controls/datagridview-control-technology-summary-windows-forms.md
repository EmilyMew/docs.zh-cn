---
title: DataGridView 控件技术摘要（Windows 窗体）
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- data grids [Windows Forms], about data grids
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
ms.openlocfilehash: 9a1738e8be0471e24744a440fee10e5b1152ab10
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717630"
---
# <a name="datagridview-control-technology-summary-windows-forms"></a>DataGridView 控件技术摘要（Windows 窗体）
本主题概述了 `DataGridView` 控件及支持其使用的类的相关信息。  
  
 以表格格式显示数据是有可能频繁执行的任务。 `DataGridView`控件设计为在网格中显示数据的完整解决方案。  
  
## <a name="keywords"></a>关键字  
 DataGridView、 BindingSource、 表、 单元格、 数据绑定、 虚拟模式  
  
## <a name="namespaces"></a>命名空间  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
 <xref:System.Data?displayProperty=nameWithType>  
  
## <a name="related-technologies"></a>相关技术  
 `BindingSource`  
  
## <a name="background"></a>背景  
 用户界面 (UI) 设计器经常发现需要向用户显示表格数据。 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]提供多种方式来在表或网格中显示数据。 `DataGridView`控件表示此技术的 Windows 窗体应用程序的最新演变。  
  
 `DataGridView`控件可以显示的数据存储区中的数据行。 支持许多类型的数据存储。 数据存储区可以容纳简单、 非类型化数据，例如一维数组，或它可以保存类型化的数据，如<xref:System.Data.DataSet>。 有关详细信息，请参阅[如何：将数据绑定到 Windows 窗体 DataGridView 控件](how-to-bind-data-to-the-windows-forms-datagridview-control.md)。  
  
 `DataGridView` 控件提供一种以表格格式显示数据的功能强大且灵活的方法。 可以使用控件来显示规模从小到大数据集的只读或可编辑视图。  
  
 您可以扩展`DataGridView`以多种方式来构建到应用程序的自定义行为的控件。 例如，可以以编程方式指定自己的排序算法，并且可以创建自己的单元格类型。 可以通过在多个属性之间进行选择来轻松地自定义 `DataGridView` 控件的外观。 许多类型的数据存储可用作数据源，或`DataGridView`控件可以不使用绑定到该数据源进行操作。  
  
## <a name="implementing-datagridview-classes"></a>实现 DataGridView 类  
 有几种方法，以便充分利用`DataGridView`控件的可扩展性功能。 你可以自定义事件和属性，通过该控件的许多方面，但某些自定义要求你创建新的类派生自现有`DataGridView`类。  
  
 最常用的基类`DataGridViewCell`和`DataGridViewColumn`。 可以派生您自己的单元格类从`DataGridViewCell`或任何其子类。 虽然可以将任何单元格类型添加到任何列，您将通常也派生的伴生列类从`DataGridViewColumn`承载自定义单元格类型的单元格的默认值。  
  
 您可以实现`IDataGridViewEditingCell`接口派生的单元格类创建具有编辑功能，但未承载的控件处于编辑模式的单元格类型中。 若要创建可以在编辑模式中的单元格承载的控件，可以实现`IDataGridViewEditingControl`类中的接口派生自<xref:System.Windows.Forms.Control>。  
  
 有关详细信息，请参阅[如何：自定义单元格和列在 Windows 窗体 DataGridView 控件通过扩展行为和外观](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)和[如何：Windows 窗体 DataGridView 单元格中承载控件](how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
## <a name="datagridview-classes-at-a-glance"></a>DataGridView 类简介  
 <xref:System.Windows.Forms>  
  
|技术范围|类/接口/配置元素|  
|---------------------|-------------------------------------------------|  
|数据绑定|<xref:System.Windows.Forms.BindingSource>|  
|数据演示文稿|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> 派生类<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> 派生类<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 派生类<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> 可扩展性|<xref:System.Windows.Forms.DataGridViewCell> 派生类<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> 派生类<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## <a name="whats-new"></a>新增功能  
 <xref:System.Windows.Forms.DataGridView>控件旨在作为完整的解决方案，用于显示与 Windows 窗体的表格数据。 应考虑使用<xref:System.Windows.Forms.DataGridView>控件，然后再其他解决方案，如<xref:System.Windows.Forms.DataGrid>，当您正在创作新的应用程序。 有关详细信息，请参阅 [Windows 窗体 DataGridView 控件与 DataGrid 控件之间的区别](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 <xref:System.Windows.Forms.DataGridView>控件可以工作与关闭结合<xref:System.Windows.Forms.BindingSource>组件。 此组件设计为窗体的主数据源。 它可以管理之间的交互<xref:System.Windows.Forms.DataGridView>控件和其数据源，而不考虑数据源类型。  
  
## <a name="see-also"></a>请参阅
- [DataGridView 控件概述](datagridview-control-overview-windows-forms.md)
- [DataGridView 控件体系结构](datagridview-control-architecture-windows-forms.md)
- [保护连接信息](../../data/adonet/protecting-connection-information.md)
