---
title: 如何：设置 Windows 窗体 DataGridView 控件中列的排序模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 4894de00a323f70ca244ea877101a5af1cbb37e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096363"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>如何：设置 Windows 窗体 DataGridView 控件中列的排序模式
在<xref:System.Windows.Forms.DataGridView>控件中，文本框列使用自动排序默认情况下，而其他列类型不会自动排序。 有时想要重写这些默认值。 例如，可以显示图像以代替文本、 数字或枚举单元格的值。 映像不能进行排序，而它们所代表的基础值可以进行排序。  
  
 在中<xref:System.Windows.Forms.DataGridView>控件，<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>列的属性值确定其排序行为。  
  
 下面的过程演示`Priority`从列[如何：自定义 Windows 窗体 DataGridView 控件中的数据格式设置](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)。 此列是 image 列，不是默认情况下可排序。 它包含的都是字符串，但是，实际的单元值，因此可以自动进行排序。  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>若要设置某一列的排序模式  
  
-   设置 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> 属性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件，其包含一个名为 `Priority` 的列。  
  
-   对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [在 Windows 窗体 DataGridView 控件中对数据进行排序](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的列排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [如何：在 Windows 窗体 DataGridView 控件中自定义排序](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
