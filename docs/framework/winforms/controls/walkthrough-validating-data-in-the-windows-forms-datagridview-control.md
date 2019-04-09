---
title: 演练：验证 Windows 窗体 DataGridView 控件中的数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: a9572bf469f539fdf52f414b2e0b6aa10f7ea288
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127343"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>演练：验证 Windows 窗体 DataGridView 控件中的数据
向用户显示数据条目的功能，经常需要验证你的窗体中输入的数据。 <xref:System.Windows.Forms.DataGridView>类提供了方便地在数据提交到数据存储区之前执行验证。 可以通过处理在验证数据<xref:System.Windows.Forms.DataGridView.CellValidating>事件，引发的<xref:System.Windows.Forms.DataGridView>当前单元格发生更改时。  
  
 在本演练中，您将检索中的行`Customers`Northwind 示例数据库中表，然后将它们显示在<xref:System.Windows.Forms.DataGridView>控件。 当用户编辑中的单元格`CompanyName`列，尝试将单元格，保留<xref:System.Windows.Forms.DataGridView.CellValidating>事件处理程序将检查新的公司名称字符串，以确保它不为空; 如果新值为空字符串，<xref:System.Windows.Forms.DataGridView>将阻止用户的光标从离开该单元格，直到输入一个非空字符串。  
  
 要将本主题中的代码作为单个列表进行复制，请参阅[如何：验证 Windows 窗体 DataGridView 控件中的数据](how-to-validate-data-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="prerequisites"></a>系统必备  
 若要完成本演练，你将需要：  
  
-   对具有 Northwind SQL Server 示例数据库的服务器的访问。  
  
## <a name="creating-the-form"></a>创建窗体  
  
#### <a name="to-validate-data-entered-in-a-datagridview"></a>若要验证在 DataGridView 中输入数据  
  
1.  创建派生的类<xref:System.Windows.Forms.Form>并且包含<xref:System.Windows.Forms.DataGridView>控件和一个<xref:System.Windows.Forms.BindingSource>组件。  
  
     下面的代码示例提供了基本的初始化，并包括`Main`方法。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]  
  
2.  用于处理连接到数据库的详细信息窗体的类定义中实现的方法。  
  
     此代码示例使用`GetData`方法，它返回已填充<xref:System.Data.DataTable>对象。 请确保您设置`connectionString`变量为适合于您的数据库的值。  
  
    > [!IMPORTANT]
    >  将敏感信息（如密码）存储在连接字符串中可能会影响应用程序的安全性。 使用 Windows 身份验证，也称为集成安全性，是更安全的方式来控制对数据库的访问。 有关详细信息，请参阅[保护连接信息](../../data/adonet/protecting-connection-information.md)。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]  
  
3.  实现窗体的一个处理程序<xref:System.Windows.Forms.Form.Load>初始化的事件<xref:System.Windows.Forms.DataGridView>和<xref:System.Windows.Forms.BindingSource>和数据绑定设置。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]  
  
4.  实现的处理程序<xref:System.Windows.Forms.DataGridView>控件的<xref:System.Windows.Forms.DataGridView.CellValidating>和<xref:System.Windows.Forms.DataGridView.CellEndEdit>事件。  
  
     <xref:System.Windows.Forms.DataGridView.CellValidating>事件处理程序，确定是否在单元格的值`CompanyName`列为空。 如果单元格的值未通过验证，则设置<xref:System.ComponentModel.CancelEventArgs.Cancel%2A>的属性<xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType>类到`true`。 这将导致<xref:System.Windows.Forms.DataGridView>控制，以阻止光标离开该单元格。 设置<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>到说明性字符串的行上的属性。 这将显示错误图标，包含错误文本的工具提示。 在中<xref:System.Windows.Forms.DataGridView.CellEndEdit>事件处理程序设置<xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A>属性为空字符串的行。 <xref:System.Windows.Forms.DataGridView.CellEndEdit>仅当该单元格退出编辑模式下，如果它未通过验证，无法执行发生的事件。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]  
  
## <a name="testing-the-application"></a>测试应用程序  
 现在可以测试窗体，以确保其行为符合预期。  
  
#### <a name="to-test-the-form"></a>若要测试窗体  
  
-   编译并运行该应用程序。  
  
     你将看到<xref:System.Windows.Forms.DataGridView>中的数据填充`Customers`表。 当双击中的单元格`CompanyName`列中，可以编辑的值。 如果你删除所有字符并按 TAB 键退出单元格，<xref:System.Windows.Forms.DataGridView>会阻止你退出。 在单元格中，键入一个非空字符串时<xref:System.Windows.Forms.DataGridView>控件，可以退出单元格。  
  
## <a name="next-steps"></a>后续步骤  
 此应用程序为您提供了一个基本的了解<xref:System.Windows.Forms.DataGridView>控件的功能。 你可以自定义外观和行为<xref:System.Windows.Forms.DataGridView>控制几种方式：  
  
-   更改边框和标头的样式。 有关详细信息，请参阅[如何：更改边框和网格线的样式中的 Windows 窗体 DataGridView 控件](change-the-border-and-gridline-styles-in-the-datagrid.md)。  
  
-   启用或限制的用户输入<xref:System.Windows.Forms.DataGridView>控件。 有关详细信息，请参阅[如何：防止行中添加和删除 Windows 窗体 DataGridView 控件](prevent-row-addition-and-deletion-datagridview.md)，和[如何：将列设为只读、 只在 Windows 窗体 DataGridView 控件](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)。  
  
-   检查用户输入与数据库相关的错误。 有关详细信息，请参见[演练：在 Windows 中的数据输入时发生的错误处理窗体 DataGridView 控件](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)。  
  
-   处理极大型数据集使用的虚拟模式。 有关详细信息，请参见[演练：在 Windows 中实现虚拟模式窗体 DataGridView 控件](implementing-virtual-mode-wf-datagridview-control.md)。  
  
-   自定义单元格的外观。 有关详细信息，请参阅[如何：自定义 Windows 窗体 DataGridView 控件中单元格的外观](customize-the-appearance-of-cells-in-the-datagrid.md)和[如何：在 Windows 窗体 DataGridView 控件中设置字体和颜色样式](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Windows 窗体 DataGridView 控件中的数据输入](data-entry-in-the-windows-forms-datagridview-control.md)
- [如何：验证 Windows 窗体 DataGridView 控件中的数据](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [演练：处理在 Windows 窗体 DataGridView 控件中输入数据时发生的错误](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [保护连接信息](../../data/adonet/protecting-connection-information.md)
