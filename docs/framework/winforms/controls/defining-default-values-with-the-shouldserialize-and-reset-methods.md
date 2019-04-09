---
title: 使用 ShouldSerialize 和 Reset 方法定义默认值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property methods
- ShouldPersist method
ms.assetid: 7b6c5e00-3771-46b4-9142-5a80d5864a5e
ms.openlocfilehash: f1f5a668c5d4f52ef7dd9f60a31c04f2173165f6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090610"
---
# <a name="defining-default-values-with-the-shouldserialize-and-reset-methods"></a>使用 ShouldSerialize 和 Reset 方法定义默认值
`ShouldSerialize` 和`Reset`是可以提供的属性的可选方法，如果相应属性不具有简单的默认值。 如果该属性具有简单的默认值，则应该应用<xref:System.ComponentModel.DefaultValueAttribute>并改为提供给特性类构造函数的默认值。 任何机制可以在设计器中的使用下列功能：  
  
-   如果已修改从其默认值，则属性提供属性浏览器中的可视指示。  
  
-   用户可以在属性上右键单击并选择**重置**将该属性还原为其默认值。  
  
-   在设计器生成更高效的代码。  
  
    > [!NOTE]
    >  请应用<xref:System.ComponentModel.DefaultValueAttribute>或提供`Reset` *PropertyName*并`ShouldSerialize` *PropertyName*方法。 不要同时使用。  
  
 `Reset` *PropertyName*方法将属性设置为其默认值，如下面的代码段中所示。  
  
```vb  
Public Sub ResetMyFont()  
   MyFont = Nothing  
End Sub  
```  
  
```csharp  
public void ResetMyFont() {  
   MyFont = null;  
}  
```  
  
> [!NOTE]
>  如果属性不具有`Reset`方法中，未标有<xref:System.ComponentModel.DefaultValueAttribute>，并且没有在其声明中提供的默认值`Reset`选项的快捷菜单中禁用该属性**属性** Visual Studio 中的 Windows 窗体设计器窗口。  
  
 使用设计器，例如 Visual Studio `ShouldSerialize` *PropertyName*方法检查属性已更改其默认值，并编写代码到窗体仅当属性已更改，从而允许更高效的代码生成。 例如：  
  
```vb  
'Returns true if the font has changed; otherwise, returns false.  
' The designer writes code to the form only if true is returned.  
Public Function ShouldSerializeMyFont() As Boolean  
   Return Not (thefont Is Nothing)  
End Function  
```  
  
```csharp  
// Returns true if the font has changed; otherwise, returns false.  
// The designer writes code to the form only if true is returned.  
public bool ShouldSerializeMyFont() {  
   return thefont != null;  
}  
```  
  
 以下是一个完整的代码示例。  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.Windows.Forms  
Imports System.Drawing  
  
Public Class MyControl  
   Inherits Control  
  
   ' Declare an instance of the Font class  
   ' and set its default value to Nothing.  
   Private thefont As Font = Nothing  
  
   ' The MyFont property.   
   Public Property MyFont() As Font  
      ' Note that the Font property never  
      ' returns null.  
      Get  
         If Not (thefont Is Nothing) Then  
            Return thefont  
         End If  
         If Not (Parent Is Nothing) Then  
            Return Parent.Font  
         End If  
         Return Control.DefaultFont  
      End Get  
      Set  
         thefont = value  
      End Set  
   End Property  
  
   Public Function ShouldSerializeMyFont() As Boolean  
      Return Not (thefont Is Nothing)  
   End Function  
  
   Public Sub ResetMyFont()  
      MyFont = Nothing  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Windows.Forms;  
using System.Drawing;  
  
public class MyControl : Control {  
   // Declare an instance of the Font class  
   // and set its default value to null.  
   private Font thefont = null;  
  
   // The MyFont property.      
   public Font MyFont {  
      // Note that the MyFont property never  
      // returns null.  
      get {  
         if (thefont != null) return thefont;  
         if (Parent != null) return Parent.Font;  
         return Control.DefaultFont;  
      }  
      set {  
         thefont = value;  
      }  
   }  
  
   public bool ShouldSerializeMyFont() {  
      return thefont != null;  
   }  
  
   public void ResetMyFont() {  
      MyFont = null;  
   }  
}  
```  
  
 在本例中为私有变量的值进行访问时，甚至`MyFont`属性是`null`，在属性浏览器不会显示`null`; 相反，它将显示<xref:System.Windows.Forms.Control.Font%2A>的父对象，如果不是`null`，或默认值<xref:System.Windows.Forms.Control.Font%2A>中定义值<xref:System.Windows.Forms.Control>。 因此的默认值为`MyFont`不能只需设置，和一个<xref:System.ComponentModel.DefaultValueAttribute>不能应用于此属性。 相反，`ShouldSerialize`并`Reset`必须为实现方法`MyFont`属性。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体控件中的属性](properties-in-windows-forms-controls.md)
- [定义属性](defining-a-property-in-windows-forms-controls.md)
- [属性更改事件](property-changed-events.md)
