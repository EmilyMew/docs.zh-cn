---
title: 如何：指定 Windows 窗体 DataGridView 控件的编辑模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 7cb9278cd311d211ef95df238b930970ae472d05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080392"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>如何：指定 Windows 窗体 DataGridView 控件的编辑模式
默认情况下，用户可以编辑的当前内容<xref:System.Windows.Forms.DataGridView>通过在其中键入内容或按 F2 的文本框单元。 这使该单元格进入编辑模式为如果满足所有以下条件：  
  
-   基础数据源支持编辑。  
  
-   <xref:System.Windows.Forms.DataGridView>启用控件。  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A>属性值不是<xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>。  
  
-   `ReadOnly`单元格、 行、 列和控件的属性都设置为`false`。  
  
 在编辑模式下，用户可以更改单元格的值，然后按 enter 键以提交更改或 ESC 键恢复到其原始值的单元格。  
  
 你可以配置<xref:System.Windows.Forms.DataGridView>控件，以便在单元格进入编辑模式，只要它成为当前的单元格。 在这种情况下，不变的 ENTER 和 ESC 键的行为，但此单元格处于编辑模式后的值是已提交或还原。 此外可以配置该控件，以便仅在单元格或仅当用户按 F2 用户键入时，单元格进入编辑模式。 最后，可以防止单元格进入编辑模式，除非在调用<xref:System.Windows.Forms.DataGridView.BeginEdit%2A>方法。  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>若要更改 DataGridView 控件的编辑模式  
  
-   设置<xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>属性设置为相应<xref:System.Windows.Forms.DataGridViewEditMode>枚举。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
-   对 <xref:System> 和 <xref:System.Windows.Forms> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Windows 窗体 DataGridView 控件中的数据输入](data-entry-in-the-windows-forms-datagridview-control.md)
