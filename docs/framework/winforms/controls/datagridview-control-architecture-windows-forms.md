---
title: DataGridView 控件体系结构（Windows 窗体）
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 892168ec282fbf168c43515e0718fe5486a345a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130255"
---
# <a name="datagridview-control-architecture-windows-forms"></a>DataGridView 控件体系结构（Windows 窗体）
<xref:System.Windows.Forms.DataGridView>控件和及其相关的类设计用于灵活、 可扩展的系统，用于显示和编辑表格数据。 这些类都包含在<xref:System.Windows.Forms?displayProperty=nameWithType>命名空间，并且它们都命名为"DataGridView"前缀。  
  
## <a name="architecture-elements"></a>体系结构元素  
 在主<xref:System.Windows.Forms.DataGridView>伴生类派生<xref:System.Windows.Forms.DataGridViewElement>。 下面的对象模型说明了<xref:System.Windows.Forms.DataGridViewElement>继承层次结构。  
  
 ![显示 DataGridViewElement 对象模型层次结构的关系图。](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewElement>类提供了对父级的引用<xref:System.Windows.Forms.DataGridView>控件并具有<xref:System.Windows.Forms.DataGridViewElement.State%2A>属性，其中包含一个值，表示中值的组合<xref:System.Windows.Forms.DataGridViewElementStates>枚举。  
  
 以下各节介绍<xref:System.Windows.Forms.DataGridView>伴生类中更多详细信息。  
  
### <a name="datagridviewelementstates"></a>DataGridViewElementStates  
 <xref:System.Windows.Forms.DataGridViewElementStates>枚举包含的以下值：  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 此枚举的值可以组合使用按位逻辑运算，因此<xref:System.Windows.Forms.DataGridViewElement.State%2A>属性可以表示多个状态在一次。 例如，<xref:System.Windows.Forms.DataGridViewElement>可同时处于<xref:System.Windows.Forms.DataGridViewElementStates.Frozen>， <xref:System.Windows.Forms.DataGridViewElementStates.Selected>，和<xref:System.Windows.Forms.DataGridViewElementStates.Visible>。  
  
### <a name="cells-and-bands"></a>单元格和带区  
 <xref:System.Windows.Forms.DataGridView>控件包含两种基本类型的对象： 单元格和带区。 从派生的所有单元格<xref:System.Windows.Forms.DataGridViewCell>基类。 两种类型的带区，<xref:System.Windows.Forms.DataGridViewColumn>并<xref:System.Windows.Forms.DataGridViewRow>，同时从派生<xref:System.Windows.Forms.DataGridViewBand>基类。  
  
 <xref:System.Windows.Forms.DataGridView>控件与多个类，互操作，但最常见<xref:System.Windows.Forms.DataGridViewCell>， <xref:System.Windows.Forms.DataGridViewColumn>，和<xref:System.Windows.Forms.DataGridViewRow>。  
  
### <a name="datagridviewcell"></a>DataGridViewCell  
 该单元格是交互的基本单位<xref:System.Windows.Forms.DataGridView>。 显示围绕单元格，并通过的单元格通常执行数据输入。 可以通过使用访问的单元格<xref:System.Windows.Forms.DataGridViewRow.Cells%2A>的集合<xref:System.Windows.Forms.DataGridViewRow>类，并且你可以通过使用访问选定的单元格<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>的集合<xref:System.Windows.Forms.DataGridView>控件。 下面的对象模型说明了这种用法，并显示<xref:System.Windows.Forms.DataGridViewCell>继承层次结构。  
  
 ![显示 DataGridViewCell 对象模型层次结构的关系图。](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <xref:System.Windows.Forms.DataGridViewCell>类型是一个抽象基类，从中派生所有单元格类型。 <xref:System.Windows.Forms.DataGridViewCell> 和其派生的类型不是 Windows 窗体控件，而某些承载 Windows 窗体控件。 通常由托管控件处理任何支持的单元格的编辑功能。  
  
 <xref:System.Windows.Forms.DataGridViewCell> 对象不会控制其自己的外观和绘制功能相同的方式作为 Windows 窗体控件。 相反，<xref:System.Windows.Forms.DataGridView>负责的外观及其<xref:System.Windows.Forms.DataGridViewCell>对象。 您可以会极大地影响的外观和行为的单元格与交互<xref:System.Windows.Forms.DataGridView>控件的属性和事件。 当具有特殊要求的自定义项的功能超出<xref:System.Windows.Forms.DataGridView>控件，可以实现自己的类派生自<xref:System.Windows.Forms.DataGridViewCell>或其子类之一。  
  
 以下列表列出了派生自的类<xref:System.Windows.Forms.DataGridViewCell>:  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   自定义单元格类型  
  
### <a name="datagridviewcolumn"></a>DataGridViewColumn  
 架构<xref:System.Windows.Forms.DataGridView>以表示控件的附加的数据存储区<xref:System.Windows.Forms.DataGridView>控件的列。 您可以访问<xref:System.Windows.Forms.DataGridView>控件的列使用<xref:System.Windows.Forms.DataGridView.Columns%2A>集合。 可以使用访问所选的列<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>集合。 下面的对象模型说明了这种用法，并显示<xref:System.Windows.Forms.DataGridViewColumn>继承层次结构。  
  
 ![显示 DataGridViewColumn 对象模型层次结构的关系图。](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 某些关键的单元格类型具有相应的列类型。 这些派生自<xref:System.Windows.Forms.DataGridViewColumn>基类。  
  
 以下列表列出了派生自的类<xref:System.Windows.Forms.DataGridViewColumn>:  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   自定义列类型  
  
### <a name="datagridview-editing-controls"></a>DataGridView 编辑控件  
 通常支持高级编辑功能的单元格使用派生自的 Windows 窗体控件的托管的控件。 这些控件还实现<xref:System.Windows.Forms.IDataGridViewEditingControl>接口。 下面的对象模型演示了这些控件的用法。  
  
 ![DataGridView 编辑控件对象模型层次结构的图示。](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 以下的编辑控件提供了<xref:System.Windows.Forms.DataGridView>控件：  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 有关创建自己的编辑控件的信息，请参阅[如何：Windows 窗体 DataGridView 单元格中承载控件](how-to-host-controls-in-windows-forms-datagridview-cells.md)。  
  
 下表说明了单元格类型、 列类型和编辑控件之间的关系。  
  
|单元格类型|承载的控件|列类型|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|n/a|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|不可用|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|不可用|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|n/a|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a>DataGridViewRow  
 <xref:System.Windows.Forms.DataGridViewRow>类显示记录的数据字段从数据存储到<xref:System.Windows.Forms.DataGridView>附加控件。 您可以访问<xref:System.Windows.Forms.DataGridView>通过使用控件的行<xref:System.Windows.Forms.DataGridView.Rows%2A>集合。 可以使用访问所选的行<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>集合。 下面的对象模型说明了这种用法，并显示<xref:System.Windows.Forms.DataGridViewRow>继承层次结构。  
  
 ![显示 DataGridViewRow 对象模型层次结构的关系图。](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 可以派生您自己的类型从<xref:System.Windows.Forms.DataGridViewRow>类，尽管这通常不需要。 <xref:System.Windows.Forms.DataGridView>控件具有多个与行相关的事件和自定义的行为的属性及其<xref:System.Windows.Forms.DataGridViewRow>对象。  
  
 如果启用<xref:System.Windows.Forms.DataGridView>控件的<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>属性，用于添加新行的特殊行显示为最后一行。 此行属于<xref:System.Windows.Forms.DataGridView.Rows%2A>集合，但它具有您需要注意的特殊功能。 有关详细信息，请参阅[使用 Windows 窗体 DataGridView 控件中的新记录行](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>请参阅

- [DataGridView 控件概述](datagridview-control-overview-windows-forms.md)
- [自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)
- [在 Windows 窗体 DataGridView 控件中使用新记录行](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
