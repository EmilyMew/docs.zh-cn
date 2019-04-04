---
title: 嵌套的控件结构 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: c016722332dafa3d3be91a1e9e98cc0ce9a49717
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835188"
---
# <a name="nested-control-structures-visual-basic"></a>嵌套的控件结构 (Visual Basic)
您可以控制将语句放在其他控制语句，例如`If...Then...Else`块内`For...Next`循环。 控制语句放在另一个控制语句称为*嵌套*。  
  
## <a name="nesting-levels"></a>嵌套级别  
 在 Visual Basic 中的控制结构可以嵌套到任意数量的级别。 它是常见的做法，以使嵌套的结构更具可读性的缩进的每个主体。 集成的开发环境 (IDE) 编辑器自动执行此操作。  
  
 在下面的示例中，该过程`sumRows`一起将矩阵的每个行的正元素。  
  
```vb
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 在前面的示例中，第一个`Next`语句关闭内部`For`循环，最后`Next`语句关闭外部`For`循环。  
  
 同样，在嵌套`If`语句，`End If`语句自动应用到最近的前`If`语句。 嵌套`Do`循环中类似的方式最里层可发挥作用`Loop`语句匹配最里面`Do`语句。  
  
> [!NOTE]
>  许多控件结构，当您单击某个关键字在结构中的关键字的所有突出显示。 例如，单击`If`中`If...Then...Else`构造、 的所有实例`If`， `Then`， `ElseIf`， `Else`，和`End If`构造中将突出显示。 若要将移动到下一步或上一个突出显示关键字，按 CTRL + SHIFT + 向下键或 CTRL + SHIFT + 向上键。  
  
## <a name="nesting-different-kinds-of-control-structures"></a>嵌套不同类型的控制结构  
 您可以嵌套一种类型的另一个类型内的控制结构。 下面的示例使用`With`在此块内`For Each`循环，并嵌套`If`块内`With`块。  
  
```vb
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a>重叠的控制结构  
 不能重叠控制结构。 这意味着，任何嵌套的结构必须完全包含在下一步最内层结构内。 例如，下面的排列是无效因为`For`循环将终止之前内部`With`块终止。  
  
 ![图，显示无效的嵌套的示例。](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Visual Basic 编译器检测到这种重叠的控制结构，并发出信号的编译时错误。  
  
## <a name="see-also"></a>请参阅

- [控制流](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [决策结构](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [循环结构](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [其他控件结构](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
