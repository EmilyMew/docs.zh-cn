---
title: 如何：在 Windows 窗体 DataGridView 控件的单元格中显示图像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: 90aaff419ecc2c890a8b3802f3aaf12092febb73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082988"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a>如何：在 Windows 窗体 DataGridView 控件的单元格中显示图像
图片或图形是可以在数据行中显示的值之一。 通常情况下，这些图形需要员工的照片或公司徽标的形式。  
  
 当显示中的数据并入图片很简单<xref:System.Windows.Forms.DataGridView>控件。 <xref:System.Windows.Forms.DataGridView>控件本身处理所支持的任何图像格式<xref:System.Drawing.Image>类，以及 OLE 的图片使用某些数据库格式。  
  
 如果<xref:System.Windows.Forms.DataGridView>控件的数据源包含一个映像，将自动显示<xref:System.Windows.Forms.DataGridView>控件。  
  
 下面的代码示例演示如何从嵌入的资源提取一个图标，并将其转换为 image 列的每个单元格中显示的位图。 文本单元格的值替换为相应的图像的另一个示例，请参阅[如何：自定义 Windows 窗体 DataGridView 控件中的数据格式设置](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="example"></a>示例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
-   一个名为嵌入的图标资源`tree.ico`。  
  
-   对 <xref:System?displayProperty=nameWithType><xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- [Windows 窗体 DataGridView 控件中的基本列、行和单元格功能](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [如何：在 Windows 窗体 DataGridView 控件中自定义数据格式设置](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
