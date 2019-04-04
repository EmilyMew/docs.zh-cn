---
title: Visual Basic 中的隐藏
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 9ad992a53618fa2f410e0b0fb23886c30136384f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839387"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic 中的隐藏
当两个编程元素共享相同的名称时，可以隐藏其中一个，或*卷影*，另一个。 在这种情况下，隐藏的元素不是可用于引用;相反，当你的代码使用的元素名称时，Visual Basic 编译器将其解析为隐藏的元素。  
  
## <a name="purpose"></a>用途  
 隐藏的主要目的是保护类成员的定义。 基本类可能需要进行更改，创建具有作为一个已定义的相同名称的元素。 如果发生这种情况，`Shadows`通过您的类将解析为成员的修饰符强制引用你定义，而不是新基类元素。  
  
## <a name="types-of-shadowing"></a>隐藏类型  
 元素可在两种不同方法隐藏另一个元素。 隐藏元素可以包含隐藏的元素，在这种情况下隐藏来实现的区域的子区域内声明*作用域通过*。 或派生类可以重新定义的基类，在其中完成种情况下隐藏成员*通过继承*。  
  
### <a name="shadowing-through-scope"></a>通过范围进行隐藏  
 很可能相同的模块、 类或结构具有相同名称但不同的作用域中的编程元素。 范围较窄的元素后，在这种方式中声明两个元素的代码引用它们共享的名称，隐藏的其他元素 （块范围是最小）。  
  
 例如，可以定义模块`Public`名为变量`temp`，该模块内的一个过程可以声明一个也名为的本地变量`temp`。 对引用`temp`内过程访问的同时对引用的局部变量`temp`从外部过程访问`Public`变量。 在此情况下，过程变量`temp`隐藏模块变量`temp`。  
  
 下图显示了两个变量，这两名为`temp`。 本地变量`temp`隐藏了成员变量`temp`从各自的过程中进行访问时`p`。 但是，`MyClass`关键字绕开隐藏并访问成员变量。  
  
 ![图形，该图形显示了通过范围进行隐藏。](./media/shadowing/shadow-scope-diagram.gif)
  
 通过范围进行隐藏的示例，请参阅[如何：隐藏与您的变量同名的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)。  
  
### <a name="shadowing-through-inheritance"></a>通过继承隐藏  
 如果派生的类重定义继承自基类的编程元素，重新定义的元素将隐藏原始元素。 与其他任何类型都可隐藏任何类型的声明的元素或重载元素集。 例如，`Integer`变量可以隐藏`Function`过程。 如果隐藏与另一个过程的过程，您可以使用不同的参数列表和不同的返回类型。  
  
 下图显示了一个基类`b`和派生的类`d`，它继承自`b`。 该基类定义一个名为过程`proc`，然后用相同名称的另一个过程的派生的类隐藏它。 第一个`Call`语句访问隐藏`proc`派生类中。 但是，`MyBase`关键字绕开隐藏和访问基类中隐藏的过程。  
  
 ![通过继承进行隐藏示意图](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 通过继承隐藏的示例，请参阅[如何：隐藏与您的变量同名的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)和[如何：隐藏继承的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)。  
  
#### <a name="shadowing-and-access-level"></a>隐藏和访问级别  
 隐藏元素并不总是可从使用派生的类的代码访问。 例如，可能会声明`Private`。 在这种情况下，隐藏是大大降低，则编译器将解析对它的同一元素的任何引用如果以前没有隐藏。 此元素是最少追溯时派生自隐藏类向后步骤的可访问元素。 如果隐藏的元素是一个过程，解析到最接近的可访问版本具有相同名称，参数列表中，并返回类型。  
  
 下面的示例演示三个类的继承层次结构。 每个类定义`Sub`过程`display`，并且每个派生类都隐藏`display`其基类中的过程。  
  
```  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 在前面的示例中，派生类`secondClass`shadows`display`与`Private`过程。 当模块`callDisplay`调用`display`中`secondClass`，调用代码是外部`secondClass`，因此不能访问私有`display`过程。 阴影操作失败，并且编译器解析对基类的引用`display`过程。  
  
 但是，进一步派生类`thirdClass`声明`display`作为`Public`，因此中的代码`callDisplay`可以访问它。  
  
## <a name="shadowing-and-overriding"></a>隐藏和重写  
 不要混淆隐藏和重写。 派生的类继承自基类，并同时重新定义与另一个声明的元素时将使用它们。 但是，两者之间的重大差异。 有关比较，请参阅[差异之间隐藏和重写](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)。  
  
## <a name="shadowing-and-overloading"></a>隐藏和重载  
 如果在派生类中隐藏多个元素具有的相同基类元素，隐藏的元素将变为该元素的重载的版本。 有关更多信息，请参见 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)。  
  
## <a name="accessing-a-shadowed-element"></a>访问隐藏的元素  
 当你从派生类访问的元素时，你通常要通过该派生类的当前实例通过符合条件的元素名称与`Me`关键字。 如果派生的类隐藏基类中的元素，可以通过限定其与访问基类元素`MyBase`关键字。  
  
 访问隐藏的元素的示例，请参阅[如何：访问被派生类隐藏的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)。  
  
### <a name="declaration-of-the-object-variable"></a>对象变量声明  
 如何创建对象变量还会影响是否在派生的类访问隐藏元素或隐藏的元素。 下面的示例创建两个对象从派生类，但一个对象声明为类的基类，另一个用作派生的类。  
  
```  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()   
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 在前面的示例中，变量`basObj`声明为类的基类。 分配`dervCls`到它的对象构成的扩大转换，因此有效。 但是，基本类不能访问该变量的隐藏版本`z`在派生类中，因此编译器解析`basObj.z`到原始的基类值。  
  
## <a name="see-also"></a>请参阅

- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [在 Visual Basic 中的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [扩大转换和收缩转换](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [继承的基础知识](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
