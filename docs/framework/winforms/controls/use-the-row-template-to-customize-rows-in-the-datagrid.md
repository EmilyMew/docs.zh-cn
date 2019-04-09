---
title: 如何：使用行模板自定义 Windows 窗体 DataGridView 控件中的行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: cb3a826262a49a8653e3a344bd126d434f2522dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073028"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>如何：使用行模板自定义 Windows 窗体 DataGridView 控件中的行
<xref:System.Windows.Forms.DataGridView>控件中使用行模板为基础，它将添加到该控件通过数据绑定或在调用时的所有行<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>而无需指定要使用的现有行的方法。  
  
 行模板向您提供更好地控制的外观和行为的行比<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>属性提供。 使用行模板，可以设置任何<xref:System.Windows.Forms.DataGridViewRow>属性，包括<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>。  
  
 有某些情况下，必须使用行模板来实现特定的效果。 例如，不能行高度信息存储在<xref:System.Windows.Forms.DataGridViewCellStyle>，因此必须使用行模板来更改使用的所有行的默认高度。 行模板非常有用，当您创建您自己的类派生自<xref:System.Windows.Forms.DataGridViewRow>并且你想在新行添加到控件时所使用的自定义类型。  
  
> [!NOTE]
>  添加行时仅使用行模板。 通过更改行模板，您不能更改现有行。  
  
### <a name="to-use-the-row-template"></a>若要使用行模板  
  
-   在从检索的对象上设置属性<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>属性。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   名为 `dataGridView1` 的 <xref:System.Windows.Forms.DataGridView> 控件。  
  
-   对 <xref:System?displayProperty=nameWithType><xref:System.Drawing?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [Windows 窗体 DataGridView 控件中的基本格式设置和样式设置](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)
