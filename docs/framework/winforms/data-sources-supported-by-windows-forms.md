---
title: Windows 窗体支持的数据源
ms.date: 03/30/2017
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
ms.openlocfilehash: b648d62c9128f0864d60ace1ca56700f594b78c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124613"
---
# <a name="data-sources-supported-by-windows-forms"></a>Windows 窗体支持的数据源
传统上，数据绑定已用于应用程序中充分利用数据库中存储数据。 使用 Windows 窗体数据绑定，您可以从数据库以及其他结构，如数组和集合中的数据访问数据，只要满足某些最低要求。  
  
## <a name="structures-to-bind-to"></a>将绑定到结构  
 在 Windows 窗体中可以绑定到各种结构，从简单到复杂的列表，如 ADO.NET 数据表 （复杂绑定） 的对象 （简单绑定）。 对于简单绑定，Windows 窗体上的简单对象支持绑定到的公共属性。 Windows 窗体基于列表的绑定通常需要对象支持<xref:System.Collections.IList>接口或<xref:System.ComponentModel.IListSource>接口。 此外，如果要通过绑定与<xref:System.Windows.Forms.BindingSource>组件，可以绑定到支持的对象，<xref:System.Collections.IEnumerable>接口。 有关与数据绑定相关的接口的详细信息，请参阅[与数据绑定相关的接口](interfaces-related-to-data-binding.md)。  
  
 以下列表显示了可以在 Windows 窗体中绑定到结构。  
  
 <xref:System.Windows.Forms.BindingSource>  
 一个<xref:System.Windows.Forms.BindingSource>是最常见的 Windows 窗体数据源和数据源和 Windows 窗体控件之间的代理的作用。 一般<xref:System.Windows.Forms.BindingSource>使用模式是将绑定到控件<xref:System.Windows.Forms.BindingSource>，并将绑定<xref:System.Windows.Forms.BindingSource>到数据源 （例如，ADO.NET 数据表或业务对象）。 <xref:System.Windows.Forms.BindingSource>提供服务，启用和改进的数据绑定支持级别。 例如，Windows 窗体列表都基于控件如<xref:System.Windows.Forms.DataGridView>并<xref:System.Windows.Forms.ComboBox>不直接支持绑定到<xref:System.Collections.IEnumerable>数据源但是，可以启用此方案中的通过绑定<xref:System.Windows.Forms.BindingSource>。 在这种情况下，<xref:System.Windows.Forms.BindingSource>将数据源转换为<xref:System.Collections.IList>。  
  
 简单对象  
 Windows 窗体对象使用的实例上支持数据绑定控件属性绑定到公共属性<xref:System.Windows.Forms.Binding>类型。 Windows 窗体还支持基于列表的绑定控件，例如<xref:System.Windows.Forms.ListControl>的对象实例时<xref:System.Windows.Forms.BindingSource>使用。  
  
 数组或集合  
 若要充当数据源，列表必须实现<xref:System.Collections.IList>接口; 一个示例是数组的一个实例<xref:System.Array>类。 数组的详细信息，请参阅[如何：创建对象 (Visual Basic 中) 的数组](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100))。  
  
 一般情况下，应使用<xref:System.ComponentModel.BindingList%601>时创建的对象的数据绑定的列表。 <xref:System.ComponentModel.BindingList%601> 泛型版本<xref:System.ComponentModel.IBindingList>接口。 <xref:System.ComponentModel.IBindingList>接口扩展<xref:System.Collections.IList>接口通过添加属性、 方法和双向数据绑定的事件。  
  
 <xref:System.Collections.IEnumerable>  
 Windows 窗体控件可以绑定到数据源仅支持<xref:System.Collections.IEnumerable>接口，如果它们通过绑定<xref:System.Windows.Forms.BindingSource>组件。  
  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 数据对象  
 [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 提供了许多适合绑定到数据结构。 每个在复杂程度和复杂性而异。  
  
-   <xref:System.Data.DataColumn>. 一个<xref:System.Data.DataColumn>是基本构建基块<xref:System.Data.DataTable>中的列数构成一个表。 每个<xref:System.Data.DataColumn>具有<xref:System.Data.DataColumn.DataType%2A>属性，用于确定类型的数据列保存 （例如，描述汽车的表中的汽车的品牌）。 您可以简单绑定控件 (如<xref:System.Windows.Forms.TextBox>控件的<xref:System.Windows.Forms.Control.Text%2A>属性) 到数据表中的列。  
  
-   <xref:System.Data.DataTable>. 一个<xref:System.Data.DataTable>是具有行和列的表的表示形式中[!INCLUDE[vstecado](../../../includes/vstecado-md.md)]。 数据表包含两个集合： <xref:System.Data.DataColumn>，表示给定表 （它最终确定的可以输入到该表的数据类型） 中的数据的列和<xref:System.Data.DataRow>，表示给定表中的数据行。 您可以将复杂绑定控件到数据表中包含的信息 (如绑定<xref:System.Windows.Forms.DataGridView>到数据表控件)。 但是，当绑定到<xref:System.Data.DataTable>，是实际上绑定到表的默认视图。  
  
-   <xref:System.Data.DataView>. 一个<xref:System.Data.DataView>的单个数据表可能会筛选或排序的自定义视图。 数据视图是"快照"复杂绑定控件使用的数据。 您可以简单绑定或复杂绑定到数据视图中的数据，但注意要绑定到的固定"图片"的数据而不是干净的、 不断更新数据源。  
  
-   <xref:System.Data.DataSet>. 一个<xref:System.Data.DataSet>是表、 关系和约束的数据库中的数据的集合。 您可以简单绑定或复杂绑定到数据集内的数据，但注意要绑定到默认<xref:System.Data.DataViewManager>为<xref:System.Data.DataSet>（请参阅下一步一注意点）。  
  
-   <xref:System.Data.DataViewManager>. 一个<xref:System.Data.DataViewManager>是自定义的视图的整个<xref:System.Data.DataSet>，类似于<xref:System.Data.DataView>，但其中包括各种关系。 与<xref:System.Data.DataViewManager.DataViewSettings%2A>集合，您可以设置默认筛选器和排序选项的任何视图的<xref:System.Data.DataViewManager>具有给定的表。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体数据绑定中的更改通知](change-notification-in-windows-forms-data-binding.md)
- [数据绑定和 Windows 窗体](data-binding-and-windows-forms.md)
- [Windows 窗体数据绑定](windows-forms-data-binding.md)
