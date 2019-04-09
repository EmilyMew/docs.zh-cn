---
title: 如何：使用 Windows 窗体 NumericUpDown 控件设置和返回数值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
ms.openlocfilehash: 281fbbd4459230056fcac2e6c684422c91dc0817
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119881"
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a>如何：使用 Windows 窗体 NumericUpDown 控件设置和返回数值
Windows 窗体的数值<xref:System.Windows.Forms.NumericUpDown>控件由其<xref:System.Windows.Forms.NumericUpDown.Value%2A>属性。 就像使用任何其他属性一样，您可以编写控件的值的条件测试。 一次<xref:System.Windows.Forms.NumericUpDown.Value%2A>属性设置，可以直接通过编写代码来执行操作，来调整它也可以调用<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>和<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>方法。  
  
### <a name="to-set-the-numeric-value"></a>若要设置的数字值  
  
1.  将一个值赋给<xref:System.Windows.Forms.NumericUpDown.Value%2A>属性在代码中或在属性窗口中。  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     或  
  
2.  调用<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>或<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>方法来增加或减少值中指定的数量<xref:System.Windows.Forms.NumericUpDown.Increment%2A>属性。  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a>若要返回的数值  
  
-   访问<xref:System.Windows.Forms.NumericUpDown.Value%2A>在代码中的属性。  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.NumericUpDown>
- <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>
- [NumericUpDown 控件](numericupdown-control-windows-forms.md)
- [NumericUpDown 控件概述](numericupdown-control-overview-windows-forms.md)
