---
title: 如何：控制 Windows 窗体 TextBox 控件中的插入点
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: 1fa6e8a3642086f81d0a62502d801ec6ade9b3d1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110711"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>如何：控制 Windows 窗体 TextBox 控件中的插入点
在 Windows 窗体时<xref:System.Windows.Forms.TextBox>控件首先获得焦点时，文本框中的默认值插入操作是左侧的任何现有文本。 用户可以移动插入点使用键盘或鼠标。 如果在文本框中丢失，并重新获得焦点，插入点将用户任何位置上一次放置它。  
  
 在某些情况下，此行为可能给用户带来不便。 在文字处理应用程序，用户可能希望新字符出现在任何现有的文本之后。 在数据输入应用程序中，用户可能希望新字符来替换任何现有条目。 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A>和<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>属性，你可以修改行为以满足您的目的。  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>若要控制在 TextBox 控件中的插入点  
  
1.  将 <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> 属性设置为适当的值。 零放置插入点紧挨左边的第一个字符。  
  
2.  （可选）设置<xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A>属性设置为你想要选择的文本的长度。  
  
     下面的代码始终返回为 0 的插入点。 `TextBox1_Enter`事件处理程序必须将绑定到控件; 有关详细信息，请参阅[在 Windows 窗体中创建事件处理程序](../creating-event-handlers-in-windows-forms.md)。  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>使插入点默认情况下可见  
 <xref:System.Windows.Forms.TextBox>插入点，则新的窗体仅当在默认情况下可见<xref:System.Windows.Forms.TextBox>控件是 tab 键顺序中的第一行。 否则，插入点将显示仅当为<xref:System.Windows.Forms.TextBox>使用键盘或鼠标焦点。  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>若要使文本框插入点在新的窗体上的默认情况下可见  
  
-   设置<xref:System.Windows.Forms.TextBox>控件的<xref:System.Windows.Forms.Control.TabIndex%2A>属性设置为`0`。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控件概述](textbox-control-overview-windows-forms.md)
- [如何：使用 Windows 窗体 TextBox 控件创建密码文本框](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [如何：创建只读文本框](how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：在字符串中添加引号](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows 窗体 TextBox 控件中选择文本](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows 窗体 TextBox 控件中查看多个行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
