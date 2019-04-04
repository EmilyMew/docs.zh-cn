---
title: 如何：访问被派生类 (Visual Basic) 隐藏的变量
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: a97a51d4570d87eaa873fb3152ad810f528dff46
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832172"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>如何：访问被派生类 (Visual Basic) 隐藏的变量
当在派生类中的代码访问的变量时，编译器通常解析到最接近的可访问版本，它是可访问的版本引用派生步骤最少向后访问类中。 如果在派生类中定义的变量，则代码通常会访问该定义。  
  
 如果派生的类变量隐藏基类中的变量，它会隐藏基类版本。 但是，可以通过限定其与访问基类变量`MyBase`关键字。  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>若要访问被派生类隐藏的基类变量  
  
-   在表达式或赋值语句中，变量名称前面加`MyBase`关键字和一个句点 (`.`)。  
  
     编译器解析对变量的基类版本的引用。  
  
     下面的示例说明了通过继承进行隐藏。 它使两个引用，用来访问隐藏的变量和一个绕开隐藏。  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     前面的示例中声明变量`shadowString`中类的基类和派生类中隐藏它。 该过程`showStrings`派生类中显示字符串的隐藏版本时名称`shadowString`未限定。 然后，它显示隐藏的版本时`shadowString`是使用限定`MyBase`关键字。  
  
## <a name="robust-programming"></a>可靠编程  
 减少风险的引用被隐藏变量的意外版本，则可以完全限定对隐藏变量的所有引用。 隐藏引入了多个版本具有相同名称的变量。 当代码语句引用的变量名称时，编译器将该引用解析的版本取决于代码语句的位置和限定字符串存在等因素。 这可能会增加引用了错误版本的变量的风险。  
  
## <a name="see-also"></a>请参阅

- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [在 Visual Basic 中隐藏](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [隐藏和重写之间的差异](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [如何：隐藏与您的变量同名的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [如何：隐藏继承的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [继承的基础知识](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
