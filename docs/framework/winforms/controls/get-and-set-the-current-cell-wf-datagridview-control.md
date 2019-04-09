---
title: 如何：获取和设置 Windows 窗体 DataGridView 控件中的当前单元格
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: fb71a6e3259d3007e11f528377c95a9c4cbeb023
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096974"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>如何：获取和设置 Windows 窗体 DataGridView 控件中的当前单元格
与交互<xref:System.Windows.Forms.DataGridView>通常要求您以编程方式发现哪个单元格是当前处于活动状态。 您可能还需要更改当前单元格。 你可以执行这些任务与<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>属性。  
  
> [!NOTE]
>  不能设置当前单元格的行或列中其<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>属性设置为`false`。  
  
 具体取决于<xref:System.Windows.Forms.DataGridView>控件的选择模式下，更改当前单元格可以更改所选内容。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的选择模式](selection-modes-in-the-windows-forms-datagridview-control.md)。  
  
### <a name="to-get-the-current-cell-programmatically"></a>若要以编程方式获取当前单元格  
  
-   使用<xref:System.Windows.Forms.DataGridView>控件的<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>属性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>若要以编程方式设置的当前单元格  
  
-   设置<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>属性的<xref:System.Windows.Forms.DataGridView>控件。 在下面的代码示例中，当前单元格设置为 0，第 1 列行。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   <xref:System.Windows.Forms.Button> 控件分别命名为`getCurrentCellButton`和`setCurrentCellButton`。 视觉对象中C#，必须将附加<xref:System.Windows.Forms.Control.Click>到关联的事件处理程序的代码示例中的每个按钮的事件。  
  
-   名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
-   对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Windows 窗体 DataGridView 控件中的基本列、行和单元格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的选择模式](selection-modes-in-the-windows-forms-datagridview-control.md)
