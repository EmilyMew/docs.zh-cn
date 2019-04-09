---
title: 如何：访问 Windows 窗体 DataGridViewComboBoxCell 下拉列表中的对象
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 221774895fa5867ad6ec870f7e293c9366e442f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080782"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>如何：访问 Windows 窗体 DataGridViewComboBoxCell 下拉列表中的对象
像<xref:System.Windows.Forms.ComboBox>控件，<xref:System.Windows.Forms.DataGridViewComboBoxColumn>和<xref:System.Windows.Forms.DataGridViewComboBoxCell>类型使您能够将任意对象添加到其下拉列表。 使用此功能，可以表示下拉列表中的复杂状态，而无需将相应的对象存储在单独的集合。  
  
 与不同<xref:System.Windows.Forms.ComboBox>控件，<xref:System.Windows.Forms.DataGridView>类型不具有<xref:System.Windows.Forms.ComboBox.SelectedItem%2A>用于检索当前所选的对象的属性。 相反，必须设置<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>属性设置为在业务对象上属性的名称。 当用户进行选择时，业务对象的指定的属性设置的单元格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>属性。  
  
 若要检索单元格的值，通过业务对象`ValueMember`属性必须指示该属性返回对业务对象本身的引用。 因此，如果业务对象的类型不受你控制，必须扩展通过继承的类型添加这样的属性。  
  
 以下过程演示如何填充下拉列表与业务对象和检索对象通过该单元格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>属性。  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>若要将业务对象添加到下拉列表  
  
1.  创建一个新<xref:System.Windows.Forms.DataGridViewComboBoxColumn>并填充其<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>集合。 或者，您可以将列设置<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>属性设置为业务对象的集合。 在这种情况下，但是，您不能添加"未分配"到下拉列表而无需创建相应的业务对象在集合中。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  设置 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 和 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 属性。 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> 指示在下拉列表中显示的业务对象的属性。 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> 指示返回到业务对象的引用的属性。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  请确保你的业务对象类型包含一个属性，它返回对当前实例的引用。 此属性必须具有值分配给名为<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>在上一步。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>若要检索当前所选的业务对象  
  
-   获取单元格<xref:System.Windows.Forms.DataGridViewCell.Value%2A>属性并将其转换为业务对象类型。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>示例  
 完整的示例演示如何将业务对象下拉列表中。 在示例中，<xref:System.Windows.Forms.DataGridView>控件绑定到的集合`Task`对象。 每个`Task`对象具有`AssignedTo`属性，指示`Employee`对象当前已分配给该任务。 `Assigned To`列将显示`Name`属性值为每个分配员工或"未分配的"if`Task.AssignedTo`属性值是`null`。  
  
 若要查看此示例中的行为，请执行以下步骤：  
  
1.  更改分配给在`Assigned To`通过从下拉列表中选择不同的值或按 CTRL + 0 中的组合框单元格的列。  
  
2.  单击`Generate Report`以显示当前分配。 此操作演示中的更改`Assigned To`列会自动更新`tasks`集合。  
  
3.  单击`Request Status`按钮，以调用`RequestStatus`方法的当前`Employee`该行的对象。 此示例演示已成功检索所选的对象。  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System 和 System.Windows.Forms 程序集的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [在 Windows 窗体 DataGridView 控件中显示数据](displaying-data-in-the-windows-forms-datagridview-control.md)
