---
title: 如何：使用设计器设置 Windows 窗体 DataGridView 控件的默认单元格样式和数据格式
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 0e5664707d12fd45c73f3585d07660fc732965fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179889"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用设计器设置 Windows 窗体 DataGridView 控件的默认单元格样式和数据格式
<xref:System.Windows.Forms.DataGridView>控件，可以指定默认单元格样式和单元格整个控件、 特定列、 行和列标题和交替行以创建分类帐效果的数据格式。 设置整个控件的默认样式中被重写默认情况下为列和交替行样式设置。 此外，在单独的行和单元的代码中设置的样式重写默认样式。  
  
 有关单元格样式的详细信息，请参阅[Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)。 若要设置交替行样式，请参阅[如何：设置 Windows 窗体 DataGridView 控件使用设计器的交替行样式](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)。  
  
 您还可以设置使用的样式<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>属性以影响将添加到控件的所有行。 有关行模板的详细信息，请参阅[如何：使用行模板自定义 Windows 窗体 DataGridView 控件中的行](use-the-row-template-to-customize-rows-in-the-datagrid.md)。  
  
 下面的过程要求**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.DataGridView>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>若要在控件中设置的所有单元格的默认样式  
  
1.  选择<xref:System.Windows.Forms.DataGridView>控件在设计器中的。  
  
2.  在中**属性**窗口中，单击省略号按钮 (![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁边<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>， <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>，或<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>属性。 **CellStyle 生成器**对话框随即出现。  
  
3.  通过设置属性，请使用定义的样式**预览版**窗格，以确认所做的选择。  
  
> [!NOTE]
>  如果启用了可视样式，行和列标题 (除<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) 样式将自动由当前主题中，重写<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>和<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>属性值。  
>   
>  可以设置为多个选定的单元格样式<xref:System.Windows.Forms.DataGridView>控制是否使用设计器中的，但如果你想要修改的单元格样式属性的值相同。 如果该属性的任何单元格样式不同**属性**的 windows **CellStyle 生成器**对话框将为空白。  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>若要设置单个列中的单元格的默认样式  
  
1.  右键单击<xref:System.Windows.Forms.DataGridView>控件在设计器中，并选择**编辑列**。  
  
2.  选择一列从**选定列**列表。  
  
3.  在中**列属性**网格中，单击省略号按钮 (![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁边<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>属性。 **CellStyle 生成器**对话框随即出现。  
  
4.  通过设置属性，请使用定义的样式**预览版**窗格，以确认所做的选择。  
  
### <a name="to-format-data-in-cells"></a>若要设置格式中的单元格的数据  
  
1.  使用上述过程之一来显示**CellStyle 生成器**对话框相关的默认单元格样式属性。  
  
2.  在中**CellStyle 生成器**对话框框中，单击省略号按钮 (![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁边<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>属性。 **格式字符串**对话框随即出现。  
  
3.  选择格式类型，然后修改的详细信息的类型 （例如要显示的小数位数），使用**示例**框以确认所做的选择。  
  
4.  如果要绑定<xref:System.Windows.Forms.DataGridView>控件与数据源可能包含 null 值，填写**Null 值**文本框。 此值将显示当单元格的值等于空引用 (`Nothing`在 Visual Basic 中) 或<xref:System.DBNull.Value?displayProperty=nameWithType>。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [如何：使用设计器设置 Windows 窗体 DataGridView 控件的交替行样式](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：向 Windows 窗体添加控件](how-to-add-controls-to-windows-forms.md)
