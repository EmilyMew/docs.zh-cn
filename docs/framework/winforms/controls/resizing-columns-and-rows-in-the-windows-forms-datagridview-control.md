---
title: 调整 Windows 窗体 DataGridView 控件中列和行的大小
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], sizing rows and columns
- columns [Windows Forms], resizing in grids
- data grids [Windows Forms], resizing columns and rows
ms.assetid: 7532764d-e5c1-4943-a08b-6377a722d3b6
ms.openlocfilehash: e1fa2d57cfb2cd374d691fe03a0e0bdbd3ad7141
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138107"
---
# <a name="resizing-columns-and-rows-in-the-windows-forms-datagridview-control"></a>调整 Windows 窗体 DataGridView 控件中列和行的大小
`DataGridView`控件提供了许多选项用于自定义其列和行的大小调整行为。 通常情况下，`DataGridView`单元格不调整大小基于其内容。 相反，它们会剪辑任何大于该单元格的显示值。 如果内容可以显示为一个字符串，该单元格工具提示中显示它。  
  
 默认情况下，用户可以拖动行、 列和标头上，以显示详细信息的分隔线。 用户也可双击分隔条可以自动调整大小以适应内容的相关联的行、 列或标头带区。  
  
 `DataGridView`控件提供属性、 方法和事件，使你能够自定义或禁用所有用户定向行为。 此外，可以以编程方式调整大小的行、 列和标头以适应其内容，也可以配置它们时更改其内容自动调整自身大小。 此外可以配置要自动将你指定的比例中的控件的可用宽度的列。  
  
## <a name="in-this-section"></a>本节内容  
 [Windows 窗体 DataGridView 控件中的大小调整选项](sizing-options-in-the-windows-forms-datagridview-control.md)  
 介绍了用于调整行、 列和标头。 此外提供了详细信息与大小相关的属性和方法，并描述了常见使用方案。  
  
 [Windows 窗体 DataGridView 控件中的列填充模式](column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 描述列填充模式中详细信息，并提供可用来试用列填充模式和其他模式的演示代码。  
  
 [如何：设置 Windows 窗体 DataGridView 控件的大小调整模式](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)  
 介绍如何为常见用途配置的大小调整模式。  
  
 [如何：以编程方式调整单元格的大小来适应 Windows 窗体 DataGridView 控件中的内容](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)  
 提供可用于试验以编程方式调整大小的演示代码。  
  
 [如何：自动调整单元格的大小来适应 Windows 窗体 DataGridView 控件中的内容变化](automatically-resize-cells-when-content-changes-in-the-datagrid.md)  
 提供可用于试验自动调整大小模式的演示代码。  
  
## <a name="reference"></a>参考  
 <xref:System.Windows.Forms.DataGridView>  
 提供关于 <xref:System.Windows.Forms.DataGridView> 控件的参考文档。  
  
## <a name="see-also"></a>请参阅

- [DataGridView 控件](datagridview-control-windows-forms.md)
