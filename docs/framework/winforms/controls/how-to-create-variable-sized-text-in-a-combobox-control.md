---
title: 如何：在 ComboBox 控件中创建大小可变的文本
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: 9155893b3d47707e0e55ee33e30d7998654f9e93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085605"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>如何：在 ComboBox 控件中创建大小可变的文本
此示例演示自定义绘图中的文本<xref:System.Windows.Forms.ComboBox>控件。 在项符合特定条件时，它是绘制中的较大图标，打开红色。  
  
## <a name="example"></a>示例  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   Windows 窗体。  
  
-   一个<xref:System.Windows.Forms.ComboBox>名为控件`ListBox1`与中的三个项<xref:System.Windows.Forms.ComboBox.Items%2A>属性。 在此示例中，三个项名为`"One", Two", and Three"`。 <xref:System.Windows.Forms.ComboBox.DrawMode%2A>的属性`ComboBox1`必须设置为<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>。  
  
    > [!NOTE]
    >  此方法也是适用于<xref:System.Windows.Forms.ListBox>控件，可以替换<xref:System.Windows.Forms.ListBox>为<xref:System.Windows.Forms.ComboBox>。  
  
-   对 <xref:System.Windows.Forms?displayProperty=nameWithType> 和 <xref:System.Drawing?displayProperty=nameWithType> 命名空间的引用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [具有内置所有者描述支持的控件](controls-with-built-in-owner-drawing-support.md)
- [ListBox 控件](listbox-control-windows-forms.md)
- [ComboBox 控件](combobox-control-windows-forms.md)
