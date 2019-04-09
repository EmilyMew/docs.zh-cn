---
title: 自定义 Windows 窗体 DataGridView 控件
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: ab8d1f07c608aca4f14f5e73860f8c3e263a4610
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091377"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a>自定义 Windows 窗体 DataGridView 控件
`DataGridView`控件提供了可用于调整的外观和其单元格、 行和列的基本行为 （外观和感受） 的多个属性。 如果您有特殊需求，超出的能力<xref:System.Windows.Forms.DataGridViewCellStyle>类中，但是，还可以实现所有者描述控件或通过创建自定义单元格、 列和行来扩展其功能。  
  
 若要绘制单元格和行自己，可以处理各种`DataGridView`绘制事件。 若要修改现有功能，或提供了新功能，可以创建自己的类型派生自现有`DataGridViewCell`， `DataGridViewColumn`，和`DataGridViewRow`类型。 此外可以通过创建显示控件的单元格处于编辑模式时所选的派生的类型提供新的编辑功能。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：自定义 Windows 窗体 DataGridView 控件中单元格的外观](customize-the-appearance-of-cells-in-the-datagrid.md)  
 描述如何处理<xref:System.Windows.Forms.DataGridView.CellPainting>手动事件，以绘制单元格。  
  
 [如何：自定义 Windows 窗体 DataGridView 控件中行的外观](customize-the-appearance-of-rows-in-the-datagrid.md)  
 描述如何处理<xref:System.Windows.Forms.DataGridView.RowPrePaint>和<xref:System.Windows.Forms.DataGridView.RowPostPaint>事件以绘制自定义的渐变背景的行和内容的跨多个列。  
  
 [如何：通过扩展 Windows 窗体 DataGridView 控件中单元格和列的行为和外观对其进行自定义](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 介绍如何创建自定义的类型派生自`DataGridViewCell`和`DataGridViewColumn`以便当鼠标指针停留在其上突出显示的单元格。  
  
 [如何：禁用 Windows 窗体 DataGridView 控件的按钮列中的按钮](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 介绍如何创建自定义的类型派生自<xref:System.Windows.Forms.DataGridViewButtonCell>和<xref:System.Windows.Forms.DataGridViewButtonColumn>为了在按钮列中显示禁用的按钮。  
  
 [如何：在 Windows 窗体 DataGridView 单元格中托管控件](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 介绍了如何实现`IDataGridViewEditingControl`接口，并创建自定义的类型派生自`DataGridViewCell`并`DataGridViewColumn`以便显示<xref:System.Windows.Forms.DateTimePicker>控件处于编辑模式时单元格。  
  
## <a name="reference"></a>参考  
 <xref:System.Windows.Forms.DataGridView>  
 提供关于 <xref:System.Windows.Forms.DataGridView> 控件的参考文档。  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 为提供参考文档<xref:System.Windows.Forms.DataGridViewCell>类。  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 为提供参考文档<xref:System.Windows.Forms.DataGridViewRow>类。  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 为提供参考文档<xref:System.Windows.Forms.DataGridViewColumn>类。  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 为提供参考文档<xref:System.Windows.Forms.IDataGridViewEditingControl>接口。  
  
## <a name="related-sections"></a>相关章节  
 [Windows 窗体 DataGridView 控件中的基本格式设置和样式设置](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 提供一些主题，描述如何修改该控件的基本外观和单元数据的显示格式。  
  
## <a name="see-also"></a>请参阅

- [DataGridView 控件](datagridview-control-windows-forms.md)
- [Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)
