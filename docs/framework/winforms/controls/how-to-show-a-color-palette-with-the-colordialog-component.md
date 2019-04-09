---
title: 如何：使用 ColorDialog 组件显示调色板
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- palettes [Windows Forms], showing color
- color dialog box [Windows Forms], showing color palettes
- colors [Windows Forms], allowing users to select
- color palettes [Windows Forms], dialog box
- ColorDialog component [Windows Forms], showing color palettes
- color palettes [Windows Forms], showing in ColorDialog component
- colors [Windows Forms], showing palettes
ms.assetid: ee050f61-dbc8-4436-ba22-51360981ab48
ms.openlocfilehash: fcaf5da9958cf66fb63bd753dc94cba9c10f62f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096031"
---
# <a name="how-to-show-a-color-palette-with-the-colordialog-component"></a>如何：使用 ColorDialog 组件显示调色板
[ColorDialog](colordialog-component-windows-forms.md)组件显示调色板的颜色，并返回包含用户选定的颜色的属性。  
  
### <a name="to-choose-a-color-using-the-colordialog-component"></a>若要使用 ColorDialog 组件选择颜色  
  
1.  显示对话框框中使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法。  
  
2.  使用<xref:System.Windows.Forms.DialogResult>属性来确定如何关闭对话框。  
  
3.  使用<xref:System.Windows.Forms.ColorDialog.Color%2A>属性的<xref:System.Windows.Forms.ColorDialog>组件设置所选的颜色。  
  
     在以下示例中，<xref:System.Windows.Forms.Button>控件的<xref:System.Windows.Forms.Control.Click>事件处理程序打开<xref:System.Windows.Forms.ColorDialog>组件。 当一种颜色是所选与用户单击**确定**，则<xref:System.Windows.Forms.Button>控件的背景色设置为所选颜色。 该示例假定窗体具有<xref:System.Windows.Forms.Button>控件和一个<xref:System.Windows.Forms.ColorDialog>组件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles Button1.Click  
       If ColorDialog1.ShowDialog() = DialogResult.OK Then  
          Button1.BackColor = ColorDialog1.Color  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(colorDialog1.ShowDialog() == DialogResult.OK)  
       {  
          button1.BackColor = colorDialog1.Color;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          if(colorDialog1->ShowDialog() == DialogResult::OK)  
          {  
             button1->BackColor = colorDialog1->Color;  
          }  
       }  
    ```  
  
     (Visual C#， [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 将以下代码放在窗体的构造函数，以注册事件处理程序。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=   
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ColorDialog>
- [ColorDialog 组件](colordialog-component-windows-forms.md)
