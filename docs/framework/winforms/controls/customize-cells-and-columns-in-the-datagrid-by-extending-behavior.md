---
title: 如何：通过扩展行为和外观自定义单元格和 Windows 窗体 DataGridView 控件中的列
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- columns [Windows Forms], customizing in DataGridView control
- cells [Windows Forms], customizing in DataGridView control
ms.assetid: 9b7dc7b6-5ce6-4566-9949-902f74f17a81
ms.openlocfilehash: 7ea684fd0a3f23005e70594bf1870851a3708a8c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721263"
---
# <a name="how-to-customize-cells-and-columns-in-the-windows-forms-datagridview-control-by-extending-their-behavior-and-appearance"></a>如何：通过扩展行为和外观自定义单元格和 Windows 窗体 DataGridView 控件中的列
<xref:System.Windows.Forms.DataGridView> 控件提供使用属性、事件和伴生类自定义其外观和行为的多种方式。 有时，你可能对这些功能不提供的单元格有要求。 你可以创建自己的自定义 <xref:System.Windows.Forms.DataGridViewCell> 类以提供扩展功能。  
  
 你可以通过从 <xref:System.Windows.Forms.DataGridViewCell> 基类或其派生类之一派生创建自定义 <xref:System.Windows.Forms.DataGridViewCell> 类。 尽管可以在任何类型的列中显示任何类型的单元格，但通常仍会创建一个专用于显示单元格类型的自定义 <xref:System.Windows.Forms.DataGridViewColumn> 类。 列类派生自 <xref:System.Windows.Forms.DataGridViewColumn> 或其派生类之一。  
  
 在以下代码示例中，你将创建一个名为 `DataGridViewRolloverCell` 的自定义单元格类，用于检测鼠标进入和离开单元格边界的时间。 当鼠标位于单元格的边界内时，会绘制一个内嵌的矩形。 这个新类型派生自 <xref:System.Windows.Forms.DataGridViewTextBoxCell>，在所有其他方面均表现为其基类。 伴生列类称为 `DataGridViewRolloverColumn`。  
  
 若要使用这些类，可创建一个包含 <xref:System.Windows.Forms.DataGridView> 控件的窗体，向 <xref:System.Windows.Forms.DataGridView.Columns%2A> 集合添加一个或多个 `DataGridViewRolloverColumn` 对象，并用包含值的行填充该控件。  
  
> [!NOTE]
>  如果添加空行，此示例将无法正常工作。 例如，当你通过设置 <xref:System.Windows.Forms.DataGridView.RowCount%2A> 属性将行添加到该控件时，则会创建空行。 这是因为在这种情况下添加的行将被自动共享，即在你单击一个单元格之后才会实例化 `DataGridViewRolloverCell` 对象，这就导致关联的行变为非共享。  
  
 由于这种类型的单元格自定义需要非共享行，因此其不适用于大型数据集。 有关行共享的详细信息，请参阅[缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)。  
  
> [!NOTE]
>  当从 <xref:System.Windows.Forms.DataGridViewCell> 或 <xref:System.Windows.Forms.DataGridViewColumn> 进行派生并将新属性添加到派生的类时，请确保重写 `Clone` 方法以在克隆操作过程中复制新属性。 还应调用基类的 `Clone` 方法，以便将基类的属性复制到新的单元格或列。  
  
### <a name="to-customize-cells-and-columns-in-the-datagridview-control"></a>自定义 DataGridView 控件中的单元格和列  
  
1.  从 <xref:System.Windows.Forms.DataGridViewTextBoxCell> 类型派生一个名为 `DataGridViewRolloverCell` 的新单元格类。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#201)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#201)]  
    [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#202)]
    [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#202](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#202)]  
  
2.  重写 <xref:System.Windows.Forms.DataGridViewTextBoxCell.Paint%2A> 类中的 `DataGridViewRolloverCell` 方法。 在重写时，首先调用基类实现，基类实现处理托管文本框的功能。 然后使用控件的 <xref:System.Windows.Forms.Control.PointToClient%2A> 方法，将光标位置（在屏幕坐标中）转换为 <xref:System.Windows.Forms.DataGridView> 客户端区域的坐标。 如果鼠标坐标位于单元格的边界之内，则绘制内嵌矩形。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#210)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#210](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#210)]  
  
3.  重写 `DataGridViewRolloverCell` 类中的 <xref:System.Windows.Forms.DataGridViewCell.OnMouseEnter%2A> 和 <xref:System.Windows.Forms.DataGridViewCell.OnMouseLeave%2A> 方法，以强制单元格在鼠标指针进入或离开它们时重新绘制自己。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#220)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#220)]  
  
4.  从 <xref:System.Windows.Forms.DataGridViewColumn> 类型派生一个名为 `DataGridViewRolloverCellColumn` 的新类。 在构造函数中，向其 <xref:System.Windows.Forms.DataGridViewColumn.CellTemplate%2A> 属性分配一个新的 `DataGridViewRolloverCell` 对象。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#300)]
     [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#300)]  
  
## <a name="example"></a>示例  
 完整的代码示例包含一个小型测试窗体，用于演示自定义单元格类型的行为。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/CS/rollovercell.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewRolloverCell#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewRolloverCell/VB/rollovercell.vb#000)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System、System.Windows.Forms 和 System.Drawing 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)
- [DataGridView 控件体系结构](datagridview-control-architecture-windows-forms.md)
- [Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)
- [有关缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
