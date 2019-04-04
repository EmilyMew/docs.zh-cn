---
title: 如何：隐藏继承的变量 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: 2b052b44043deba85c8b142a2bf1a684c1159809
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842507"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>如何：隐藏继承的变量 (Visual Basic)
在派生的类继承其基类的所有定义。 如果你想要定义为基的类的元素使用相同的名称的变量，则可以隐藏，或者*卷影*，当在派生类中定义您的变量时该基类元素。 如果执行此操作时，派生类中的代码访问您的变量，除非显式绕过隐藏机制。  
  
 你可能想要隐藏继承的变量的另一个原因是为了避免基类修订版本。 基本类可能需要进行更改所继承的元素的更改。 如果发生这种情况，`Shadows`修饰符强制派生类，以解析为您的变量，而不是基类元素的引用。  
  
### <a name="to-hide-an-inherited-variable"></a>若要隐藏继承的变量  
  
1.  请确保你想要隐藏的变量在类级别 （任何过程之外） 声明。 否则不需要将其隐藏。  
  
2.  在派生类中，编写[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)声明您的变量。 与继承的变量使用相同的名称。  
  
3.  包括[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)声明中的关键字。  
  
     当在派生类中的代码引用的变量名称时，编译器将解析到您的变量引用。  
  
     下面的示例演示如何隐藏被继承的变量。  
  
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
 隐藏引入了多个版本具有相同名称的变量。 当代码语句引用的变量名称时，编译器将该引用解析的版本取决于代码语句的位置和限定字符串存在等因素。 这可能会增加被隐藏变量的意外版本中引用的风险。 通过完全限定对隐藏变量的所有引用，可以降低该风险。  
  
## <a name="see-also"></a>请参阅

- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [在 Visual Basic 中隐藏](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [隐藏和重写之间的差异](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [如何：隐藏与您的变量同名的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [如何：访问被派生类隐藏的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [继承的基础知识](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
