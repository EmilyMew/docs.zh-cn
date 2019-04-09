---
title: 如何：为 Windows 窗体 DataGridView 控件设置交替行样式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: 06b93a756b351213a87e1f52bc691aaa27558ac4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078585"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>如何：为 Windows 窗体 DataGridView 控件设置交替行样式
表格数据通常以类似帐目的格式向用户显示，其中的交替行具有不同的背景色。 这种格式使用户可以更轻松地分辨每一行的单元格，尤其是有多列的宽表。  
  
 借助 <xref:System.Windows.Forms.DataGridView> 控件，可为交替行指定完整的样式信息。 这使你可以使用背景色以及样式特性（如前景色和字体）区分交替行。  
  
 Visual Studio 中对此任务提供支持。  另请参阅[如何：设置 Windows 窗体 DataGridView 控件使用设计器的交替行样式](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)。  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>若要以编程方式设置交替行样式  
  
-   设置 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 返回的 <xref:System.Windows.Forms.DataGridViewCellStyle> 对象的属性以及 <xref:System.Windows.Forms.DataGridView> 的 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> 属性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  使用 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> 和 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> 属性指定的样式会重写列上以 <xref:System.Windows.Forms.DataGridView> 级别指定的样式，但被单独的行和单元格级别上设置的样式重写。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
-   对 <xref:System?displayProperty=nameWithType><xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="robust-programming"></a>可靠编程  
 为实现最大的可伸缩性，应在使用相同样式的多个行、列或单元格间共享 <xref:System.Windows.Forms.DataGridViewCellStyle> 对象，而不是分别设置单个元素的样式属性。 有关详细信息，请参阅[缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Windows 窗体 DataGridView 控件中的基本格式设置和样式设置](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [如何：设置 Windows 窗体 DataGridView 控件中的字体和颜色样式](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
