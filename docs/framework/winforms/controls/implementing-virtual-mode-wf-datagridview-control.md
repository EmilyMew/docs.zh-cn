---
title: 演练：在 Windows 窗体 DataGridView 控件中实现虚拟模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 7509e2f5035cb05c20af379f9f6a141177d540d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127044"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>演练：在 Windows 窗体 DataGridView 控件中实现虚拟模式
如果想要显示非常大量的表格数据<xref:System.Windows.Forms.DataGridView>控件，可以设置<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>属性设置为`true`和显式管理其数据存储区与控件的交互。 这样可以微调控件在此情况下的性能。  
  
 <xref:System.Windows.Forms.DataGridView>控件提供了可以处理与自定义数据存储进行交互的多个事件。 本演练将指导您完成实现这些事件处理程序的过程。 本主题中的代码示例用于说明目的使用非常简单的数据源。 在生产设置中，通常将加载只有需要到缓存中，显示和处理的行<xref:System.Windows.Forms.DataGridView>事件进行交互并更新缓存。 有关详细信息，请参阅[实时数据加载 Windows 窗体 DataGridView 控件中实现虚拟模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 要将本主题中的代码作为单个列表进行复制，请参阅[如何：Windows 中的实现虚拟模式窗体 DataGridView 控件](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="creating-the-form"></a>创建窗体  
  
#### <a name="to-implement-virtual-mode"></a>若要实现虚拟模式  
  
1.  创建派生的类<xref:System.Windows.Forms.Form>和包含<xref:System.Windows.Forms.DataGridView>控件。  
  
     下面的代码包含一些基本的初始化。 它声明一些将在后续步骤中使用的变量，提供`Main`方法，并提供了类构造函数中的简单窗体布局。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  实现窗体的一个处理程序<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>控制，并填充具有示例值的数据存储区。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  实现的处理程序<xref:System.Windows.Forms.DataGridView.CellValueNeeded>从数据存储中检索请求的单元格的值的事件或`Customer`当前正在编辑的对象。  
  
     每当发生此事件<xref:System.Windows.Forms.DataGridView>控件需要绘制单元格。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  实现的处理程序<xref:System.Windows.Forms.DataGridView.CellValuePushed>编辑的单元格将值存储在事件`Customer`对象，表示编辑过的行。 每当用户提交一个单元格的值更改时，将发生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  实现的处理程序<xref:System.Windows.Forms.DataGridView.NewRowNeeded>创建一个新的事件`Customer`对象，表示新创建的行。  
  
     每当用户输入新记录的行，将发生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  实现的处理程序<xref:System.Windows.Forms.DataGridView.RowValidated>将新的或已修改行保存到数据存储的事件。  
  
     每当用户更改当前行时，将发生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  实现的处理程序<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件，该值指示是否<xref:System.Windows.Forms.DataGridView.CancelRowEdit>用户两次在编辑模式下或在非编辑模式，按 esc 键指示行恢复时，事件将会发生。  
  
     默认情况下<xref:System.Windows.Forms.DataGridView.CancelRowEdit>在恢复行的当前行中的任何单元格已被修改，除非时发生<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>属性设置为`true`中<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件处理程序。 在运行时确定提交作用域时，此事件非常有用。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  实现的处理程序<xref:System.Windows.Forms.DataGridView.CancelRowEdit>放弃的值的事件`Customer`对象，表示当前行。  
  
     当用户在编辑模式中两次或一次非编辑模式，按 esc 键指示行恢复时，将发生此事件。 如果没有当前行中的单元格已被修改，或如果不会发生此事件的值<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>属性已设置为`false`中<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>事件处理程序。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. 实现的处理程序<xref:System.Windows.Forms.DataGridView.UserDeletingRow>删除现有的事件`Customer`数据存储区中的对象或放弃未保存`Customer`对象，表示新创建的行。  
  
     每当用户通过单击行标题并按 DELETE 键删除行时，将发生此事件。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. 实现一个简单`Customers`类来表示此代码示例使用的数据项目。  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 现在可以测试窗体，以确保其行为符合预期。  
  
#### <a name="to-test-the-form"></a>若要测试窗体  
  
-   编译并运行该应用程序。  
  
     你将看到<xref:System.Windows.Forms.DataGridView>控件填充三个客户记录。 可以修改行中的多个单元格的值，并在编辑模式中两次，一次非编辑模式，若要还原到其原始值的整行，请按 esc 键。 当你修改、 添加或删除控件中的行时`Customer`修改、 添加或删除数据存储中的对象。  
  
## <a name="next-steps"></a>后续步骤  
 此应用程序为您提供了必须处理实现中的虚拟模式的事件的一个基本的了解<xref:System.Windows.Forms.DataGridView>控件。 您可以提高在多方面此基本应用程序：  
  
-   实现缓存来自外部数据库的值的数据存储。 缓存应检索并放弃根据需要的值，使其仅包含必要的操作时使用少量内存客户端计算机上的显示。  
  
-   对数据存储，具体取决于你的需求的性能进行微调。 例如，你可能想要通过使用更大的缓存大小和最大程度减少数据库查询的次数补偿慢速网络连接，而客户端计算机的内存限制。  
  
 有关缓存来自外部数据库的值的详细信息，请参阅[如何：实现虚拟模式在 Windows 中实时数据加载窗体 DataGridView 控件](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Windows 窗体 DataGridView 控件中的性能优化](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [缩放 Windows 窗体 DataGridView 控件的最佳做法](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [在 Windows 窗体 DataGridView 控件中实现实时数据加载的虚拟模式](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [如何：在 Windows 窗体 DataGridView 控件中实现虚拟模式](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
