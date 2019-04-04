---
title: 对象变量声明 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837645"
---
# <a name="object-variable-declaration-visual-basic"></a>对象变量声明 (Visual Basic)
正常的声明语句用于声明对象变量。 对于数据类型，您指定`Object`(即[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)) 或更具体的类是要创建该对象。  
  
 声明一个变量，作为`Object`等同于其声明为<xref:System.Object?displayProperty=nameWithType>。  
  
 具有特定的对象类的变量声明时，它可以访问所有方法和属性公开的类和它所继承的类。 如果声明的变量<xref:System.Object>，它可以访问的成员<xref:System.Object>类，除非您启用`Option Strict Off`允许后期绑定。  
  
## <a name="declaration-syntax"></a>声明语法  
 使用以下语法声明对象变量：  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 此外可以指定[公共](../../../../visual-basic/language-reference/modifiers/public.md)，[受保护](../../../../visual-basic/language-reference/modifiers/protected.md)，[友元](../../../../visual-basic/language-reference/modifiers/friend.md)， `Protected Friend`，[专用](../../../../visual-basic/language-reference/modifiers/private.md)，[共享](../../../../visual-basic/language-reference/modifiers/shared.md)，或[静态](../../../../visual-basic/language-reference/modifiers/static.md)声明中。 以下示例声明是有效的：  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>后期绑定和早期绑定  
 有时特定类是未知的代码运行之前。 在这种情况下，您必须声明对象变量与`Object`数据类型。 这将创建的常规引用到任何类型的对象，并在运行时分配特定的类。 这称为*后期绑定*。 后期绑定需要额外的执行时间。 它也会限制你的代码的方法和类，最近已向其分配的属性。 如果你的代码尝试访问不同类的成员，这可能导致运行时错误。  
  
 当在编译时知道特定的类时，应将声明为该类的对象变量。 这称为*早期绑定*。 早期绑定可以提高性能，并保证您对所有方法和属性的特定类的代码访问权限。 在前面的示例声明中，如果变量`objA`使用仅类的对象<xref:System.Windows.Forms.Label?displayProperty=nameWithType>，则应指定`As System.Windows.Forms.Label`其声明中。  
  
### <a name="advantages-of-early-binding"></a>早期绑定的优点  
 声明对象变量作为特定类具有几个优势：  
  
-   自动类型检查  
  
-   保证特定类的所有成员访问  
  
-   在代码编辑器中的 Microsoft IntelliSense 支持  
  
-   改进了的代码的可读性  
  
-   在代码中减少错误  
  
-   在捕获到错误编译时间而不是运行时  
  
-   更快地执行代码  
  
## <a name="access-to-object-variable-members"></a>对象变量的成员的访问权限  
 当`Option Strict`打开`On`，对象变量可以访问的方法和类与其声明的属性。 下面的示例阐释了这一点。  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 在此示例中， `p` 仅可使用 <xref:System.Object> 类的成员，这不包括 `Left` 属性。 另一方面， `q` 已声明为 <xref:System.Windows.Forms.Label>类型，因此它可以使用 <xref:System.Windows.Forms.Label> 命名空间中 <xref:System.Windows.Forms> 类的所有方法和属性。  
  
## <a name="flexibility-of-object-variables"></a>对象变量的灵活性  
 使用继承层次结构中的对象，可以用来声明对象变量的类的选择。 在进行选择时，必须平衡的一个类成员访问对象赋值的灵活性。 例如，考虑到会导致在继承层次结构<xref:System.Windows.Forms.Form?displayProperty=nameWithType>类：  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 假设你的应用程序定义一个名为的窗体类`specialForm`，后者又继承类<xref:System.Windows.Forms.Form>。 你可以专门引用对象变量声明`specialForm`，如下面的示例所示。  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 在前面的示例中的声明限制在变量`nextForm`到类的对象`specialForm`，但这也使得所有的方法和属性的`specialForm`供`nextForm`，以及从其的所有类的所有成员`specialForm`继承。  
  
 可以通过声明它的类型进行更一般的对象变量<xref:System.Windows.Forms.Form>，如下面的示例所示。  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 在前面的示例中的声明，可在分配到应用程序中的任何窗体`anyForm`。 但是，尽管`anyForm`可以访问的类的所有成员<xref:System.Windows.Forms.Form>，它不能使用任何其他方法或属性，例如为特定窗体定义`specialForm`。  
  
 基类的所有成员都都可用于派生类，但派生类的其他成员都将不可用到的基类。  
  
## <a name="see-also"></a>请参阅

- [对象变量](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [对象变量赋值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [对象变量值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [如何：声明对象变量并在 Visual Basic 中为其分配对象](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [如何：访问对象的成员](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New 运算符](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
