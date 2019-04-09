---
title: 如何：使用 Windows 窗体 TextBox 控件创建密码文本框
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: f2017ccfd6d8320d6afc7b5e8a2ce8349c4fbd17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110607"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>如何：使用 Windows 窗体 TextBox 控件创建密码文本框
密码框是在用户键入一个字符串时显示占位符的 Windows 窗体文本框。  
  
### <a name="to-create-a-password-text-box"></a>若要创建密码文本框  
  
1.  设置<xref:System.Windows.Forms.TextBox.PasswordChar%2A>属性的<xref:System.Windows.Forms.TextBox>控件的特定字符。  
  
     <xref:System.Windows.Forms.TextBox.PasswordChar%2A>属性指定显示在文本框中的字符。 例如，如果你想在密码框中显示星号，指定 * 为<xref:System.Windows.Forms.TextBox.PasswordChar%2A>属性窗口中的属性。 然后，用户在文本框中键入的字符，无论被显示一个星号。  
  
2.  （可选）设置<xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>属性。 属性用于确定可以在文本框中键入多少个字符。 如果超出最大长度，系统会发出提示音并在文本框中不接受任何更多的字符。 请注意，你可能想要执行此密码的最大长度为可能的黑客试图猜测密码的使用。  
  
     下面的代码示例演示如何初始化将接受多达 14 个字符的字符串并显示星号来替代字符串的文本框。 `InitializeMyControl`过程将不会自动执行; 它必须在调用。  
  
    > [!IMPORTANT]
    >  使用<xref:System.Windows.Forms.TextBox.PasswordChar%2A>属性位于文本框中可帮助确保其他人将无法再以确定它们观察用户输入其用户的密码。 此安全措施不涉及任何类型的存储或传输的可能是因为应用程序逻辑的密码。 因为输入文本不以任何方式进行加密，应将它视为，就像任何其他机密数据。 即使没有这种情况下出现，密码是仍被视为纯文本字符串 （除非您已实现了其他安全措施）。  
  
    ```vb  
    Private Sub InitializeMyControl()  
       ' Set to no text.  
       TextBox1.Text = ""  
       ' The password character is an asterisk.  
       TextBox1.PasswordChar = "*"  
       ' The control will allow no more than 14 characters.  
       TextBox1.MaxLength = 14  
    End Sub  
    ```  
  
    ```csharp  
    private void InitializeMyControl()  
    {  
       // Set to no text.  
       textBox1.Text = "";  
       // The password character is an asterisk.  
       textBox1.PasswordChar = '*';  
       // The control will allow no more than 14 characters.  
       textBox1.MaxLength = 14;  
    }  
    ```  
  
    ```cpp  
    private:  
       void InitializeMyControl()  
       {  
          // Set to no text.  
          textBox1->Text = "";  
          // The password character is an asterisk.  
          textBox1->PasswordChar = '*';  
          // The control will allow no more than 14 characters.  
          textBox1->MaxLength = 14;  
       }  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.TextBox>
- [TextBox 控件概述](textbox-control-overview-windows-forms.md)
- [如何：控制 Windows 窗体 TextBox 控件中的插入点](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [如何：创建只读文本框](how-to-create-a-read-only-text-box-windows-forms.md)
- [如何：在字符串中添加引号](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [如何：在 Windows 窗体 TextBox 控件中选择文本](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [如何：在 Windows 窗体 TextBox 控件中查看多个行](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox 控件](textbox-control-windows-forms.md)
