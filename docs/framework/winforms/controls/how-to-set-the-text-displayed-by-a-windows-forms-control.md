---
title: 如何：设置 Windows 窗体控件显示的文本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: e9bf2077f10648dbe3ebf214bbbf9546cbb398c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096181"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>如何：设置 Windows 窗体控件显示的文本
Windows 窗体控件通常会显示一些与控件的主要功能相关的文本。 例如，<xref:System.Windows.Forms.Button> 控件通常会显示一个题注，用于指示单击按钮时将执行的操作。 对于所有控件而言，都可通过使用 <xref:System.Windows.Forms.Control.Text%2A> 属性来设置或返回文本。 可以使用 <xref:System.Windows.Forms.Control.Font%2A> 属性更改字体。 还可使用设计器来设置文本。  另请参阅[如何：创建 Windows 窗体控件使用设计器的访问键](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md)，[如何：设置显示的文本的 Windows 窗体控件使用设计器](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md)，[如何：设置所显示的图像的 Windows 窗体控件使用设计器](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md)。  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>以编程方式设置控件所显示的文本  
  
1.  将 <xref:System.Windows.Forms.Control.Text%2A> 属性设置为字符串。  
  
     若要创建带下划线的访问密钥，包含一个 & 号 (&) 将访问密钥的字母前。  
  
2.  将 <xref:System.Windows.Forms.Control.Font%2A> 属性设置为类型 <xref:System.Drawing.Font> 的对象。  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  可使用转义符来显示用户界面元素中的特殊字符，通常对这些元素（如菜单项）有着不同的解释。 例如，以下代码行设置要读取的菜单项的文本"和现在的内容完全不同":  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [如何：创建 Windows 窗体控件的访问键](how-to-create-access-keys-for-windows-forms-controls.md)
- [如何：响应 Windows 窗体按钮的单击](how-to-respond-to-windows-forms-button-clicks.md)
