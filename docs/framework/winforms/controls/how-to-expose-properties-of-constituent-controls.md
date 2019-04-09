---
title: 如何：公开构成控件的属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: 750caa1f45f870e63a5b7ccbe0c309e6fb0b3178
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106348"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a>如何：公开构成控件的属性
构成复合控件的控件称为*构成控件*。 这些控件通常被声明为私有的并因此不能由开发人员访问。 如果你想要使这些控件的属性可供将来的用户，必须向用户公开它们。 通过在用户控件中，创建属性并使用公开构成控件的属性`get`和`set`该属性的访问器以构成控件的私有属性更改生效。  
  
 有一个用户控件，请考虑使用名为的构成按钮`MyButton`。 在此示例中，当用户请求`ConstituentButtonBackColor`属性中，存储中的值<xref:System.Windows.Forms.Control.BackColor%2A>属性的`MyButton`传送。 当用户将分配给此属性的值时，该值将自动传递给<xref:System.Windows.Forms.Control.BackColor%2A>的属性`MyButton`和`set`将会执行代码，更改颜色`MyButton`。  
  
 下面的示例演示如何公开<xref:System.Windows.Forms.Control.BackColor%2A>构成按钮的属性：  
  
```vb  
Public Property ButtonColor() as System.Drawing.Color  
   Get  
      Return MyButton.BackColor  
   End Get  
   Set(Value as System.Drawing.Color)  
      MyButton.BackColor = Value  
   End Set  
End Property  
```  
  
```csharp  
public Color ButtonColor  
{  
   get  
   {  
      return(myButton.BackColor);  
   }  
   set  
   {  
      myButton.BackColor = value;  
   }  
}  
```  
  
### <a name="to-expose-a-property-of-a-constituent-control"></a>若要公开构成控件的属性  
  
1.  创建你的用户控件的公共属性。  
  
2.  在`get`一部分的属性，编写代码，以检索你想要公开的属性的值。  
  
3.  在`set`一部分的属性，编写代码，将属性的值传递给构成控件的公开的属性。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.UserControl>
- [Windows 窗体控件中的属性](properties-in-windows-forms-controls.md)
- [各种自定义控件](varieties-of-custom-controls.md)
