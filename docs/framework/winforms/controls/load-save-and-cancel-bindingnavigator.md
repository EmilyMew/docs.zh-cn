---
title: 如何：向 Windows 窗体 BindingNavigator 控件添加“加载”、“保存”和“取消”按钮
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: 52d4fc32836a5d20bd99d8ebfd3119c761376e30
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098710"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a>如何：向 Windows 窗体 BindingNavigator 控件添加“加载”、“保存”和“取消”按钮
<xref:System.Windows.Forms.BindingNavigator>控件是特殊用途<xref:System.Windows.Forms.ToolStrip>旨在用于导航和操作绑定到数据窗体上的控件的控件。  
  
 因为它是<xref:System.Windows.Forms.ToolStrip>控件，<xref:System.Windows.Forms.BindingNavigator>组件可以轻松地修改为包含用户的附加或替代命令。  
  
 在下面的过程中，<xref:System.Windows.Forms.TextBox>控件绑定到数据，并<xref:System.Windows.Forms.ToolStrip>添加到窗体的控件修改以包括保存、 加载和取消按钮。  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a>若要添加负载，保存和取消按钮的 BindingNavigator 组件  
  
1.  向窗体添加一个 <xref:System.Windows.Forms.TextBox> 控件。  
  
2.  将其绑定到<xref:System.Windows.Forms.BindingSource>，后者已绑定到数据源。 此示例中，为<xref:System.Windows.Forms.BindingSource>绑定到数据库。  
  
3.  生成数据集和表适配器后，请将<xref:System.Windows.Forms.BindingNavigator>到窗体控件。  
  
4.  设置<xref:System.Windows.Forms.BindingNavigator>控件的<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>属性设置为<xref:System.Windows.Forms.BindingSource>绑定到控件的窗体上。  
  
5.  选择 <xref:System.Windows.Forms.BindingNavigator> 控件。  
  
6.  单击智能标记标志符号 (![智能标记标志符号](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，因此**BindingNavigator 任务**对话框，然后选择**编辑项**.  
  
     **项集合编辑器**出现。  
  
7.  在中**项集合编辑器**，完成下列操作：  
  
    1.  添加<xref:System.Windows.Forms.ToolStripSeparator>和三个<xref:System.Windows.Forms.ToolStripButton>通过选择适当类型的项<xref:System.Windows.Forms.ToolStripItem>，然后单击**添加**按钮。  
  
    2.  设置<xref:System.Windows.Forms.ToolStripItem.Name%2A>到按钮的属性**LoadButton**， **SaveButton**，并且**CancelButton**分别。  
  
    3.  设置<xref:System.Windows.Forms.ToolStripItem.Text%2A>到按钮的属性**负载**，**保存**，并且**取消**。  
  
    4.  设置<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>到按钮的每个属性**文本**。 或者，可以将此属性设置为**图像**或**ImageAndText**，并设置中显示的图像<xref:System.Windows.Forms.ToolStripItem.Image%2A>属性。  
  
    5.  单击**确定**以关闭对话框。这些按钮将添加到<xref:System.Windows.Forms.ToolStrip>。  
  
8.  右键单击窗体，然后选择**查看代码**。  
  
9. 在代码编辑器中，找到将数据加载到表适配器的代码的行。 此代码生成设置在步骤 2 中的数据绑定时。 代码应如下所示： `TableAdapterName.Fill(DataSetName.TableName)`。 它将很有可能是窗体的<xref:System.Windows.Forms.Form.Load>事件。  
  
10. 创建事件处理程序<xref:System.Windows.Forms.ToolStripItem.Click>的事件**负载**<xref:System.Windows.Forms.ToolStripButton>之前创建并将此数据加载代码移到它。  
  
     你的代码应类似于下面：  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. 创建事件处理程序<xref:System.Windows.Forms.ToolStripItem.Click>的事件**保存**<xref:System.Windows.Forms.ToolStripButton>之前创建和编写代码以更新表控件内的数据绑定到。  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    > 在某些情况下，<xref:System.Windows.Forms.BindingNavigator>组件已**保存**按钮，但没有代码将生成的 Windows 窗体设计器。 在这种情况下，可以将前面的代码中放置<xref:System.Windows.Forms.ToolStripItem.Click>这个按钮，而不是创建全新的按钮上的事件处理程序<xref:System.Windows.Forms.ToolStrip>。 但是，该按钮默认处于禁用状态，因此必须设置<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>属性的按钮为`true`以使按钮函数正确。
  
12. 创建事件处理程序<xref:System.Windows.Forms.ToolStripItem.Click>的事件**取消**<xref:System.Windows.Forms.ToolStripButton>之前创建和编写代码来取消对显示的数据记录的任何更改。  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的范围限定为一行数据。 保存您在导航到下一条记录之前查看该单个记录时进行任何更改。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [BindingNavigator 控件](bindingnavigator-control-windows-forms.md)
- [BindingSource 组件概述](bindingsource-component-overview.md)
