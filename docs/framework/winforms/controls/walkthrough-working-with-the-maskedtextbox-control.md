---
title: 演练：使用 MaskedTextBox 控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: ca505b062be8c60c1dd9b08fead4855eb1eb4cd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103839"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>演练：使用 MaskedTextBox 控件
本演练涉及以下任务：  
  
-   正在初始化<xref:System.Windows.Forms.MaskedTextBox>控件  
  
-   使用<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>事件处理程序来提醒用户，当一个字符不符合掩码  
  
-   分配到类型<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>属性并使用<xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted>试图提交的值不是有效的类型时向用户发出警报的事件处理程序  
  
## <a name="creating-the-project-and-adding-a-control"></a>创建项目并添加控件  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>若要向窗体添加 MaskedTextBox 控件  
  
1.  打开想要放置该窗的体<xref:System.Windows.Forms.MaskedTextBox>控件。  
  
2.  拖动<xref:System.Windows.Forms.MaskedTextBox>控件从**工具箱**向窗体。  
  
3.  右键单击该控件，然后选择**属性**。 在中**属性**窗口中，选择**掩码**属性，单击 **...** （省略号） 按钮旁边的属性名称。  
  
4.  在中**输入掩码**对话框中，选择**短日期**掩码，并单击**确定**。  
  
5.  在中**属性**窗口中设置<xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A>属性设置为`true`。 此属性会导致短的提示音，每次用户尝试输入不违反掩码定义的字符。  
  
 掩码属性支持的字符的摘要，请参阅备注部分的<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>属性。  
  
## <a name="alert-the-user-to-input-errors"></a>提醒用户输入错误  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>添加被拒绝的掩码输入的气球状提示  
  
1.  返回到**工具箱**并添加<xref:System.Windows.Forms.ToolTip>向窗体。  
  
2.  创建事件处理程序<xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected>引发的事件<xref:System.Windows.Forms.ToolTip>发生的输入的错误。 气球状提示保持可见，五秒，或直到用户单击它。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>不是有效的类型向用户发出警报  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>添加无效的数据类型的气球状提示  
  
1.  在窗体中<xref:System.Windows.Forms.Form.Load>事件处理程序分配<xref:System.Type>对象，表示<xref:System.DateTime>键入到<xref:System.Windows.Forms.MaskedTextBox>控件的<xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A>属性：  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2.  为 <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> 事件添加事件处理程序：  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.MaskedTextBox>
- [MaskedTextBox 控件](maskedtextbox-control-windows-forms.md)
