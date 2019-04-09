---
title: 如何：使用设计器设置 Windows 窗体 DataGridView 控件的交替行样式
ms.date: 03/30/2017
helpviewer_keywords:
- ledger-like formats
- DataGridView control [Windows Forms], row style alternation
- Windows Forms, rows
- rows [Windows Forms], alternating
- data [Windows Forms], displaying
ms.assetid: 02373442-bf94-4470-9f8a-e44c4a9d5b88
ms.openlocfilehash: 52105a933efc8bccde8d01aa707ade0a2af6be96
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072931"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control-using-the-designer"></a>如何：使用设计器设置 Windows 窗体 DataGridView 控件的交替行样式
表格数据通常显示其中的交替行具有不同的背景色以类似帐目的格式。 这种格式使用户可以更轻松地分辨每一行的单元格，尤其是有多列的宽表。  
  
 借助 <xref:System.Windows.Forms.DataGridView> 控件，可为交替行指定完整的样式信息。 可以使用如前景色和字体、 背景色以及样式特征来区分交替行。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
 下面的过程需要**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.DataGridView>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="define-styles-for-alternating-rows"></a>定义的交替行样式  
  
1.  选择<xref:System.Windows.Forms.DataGridView>控件在设计器中的。  
  
2.  在中**属性**窗口中，单击省略号按钮 (![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁边<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>属性。  
  
3.  在中**CellStyle 生成器**对话框中，通过设置属性，定义样式，并使用**预览**窗格，以确认所做的选择。 您指定的样式用于在控件中，从第二个显示的所有其他行。  
  
4.  若要定义的剩余行的样式，请重复步骤 2 和 3 使用<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>属性。  
  
    > [!NOTE]
    >  单元格的显示使用继承自多个属性的样式。 有关样式继承的详细信息，请参阅[Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- [Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的基本格式设置和样式设置](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [将设计器与 Windows 窗体 DataGridView 控件结合使用](using-the-designer-with-the-windows-forms-datagridview-control.md)
- [如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [如何：向 Windows 窗体添加控件](how-to-add-controls-to-windows-forms.md)
