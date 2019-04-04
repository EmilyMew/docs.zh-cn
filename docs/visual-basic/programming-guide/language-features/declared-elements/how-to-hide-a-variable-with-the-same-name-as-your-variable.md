---
title: 如何：隐藏与您的变量 (Visual Basic 中) 同名的变量
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: a8a7eda2a636d7f89131d140c82ad4f3c4743211
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826673"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>如何：隐藏与您的变量 (Visual Basic 中) 同名的变量
可以隐藏的变量*隐藏*即，它通过将它重新定义具有相同名称的变量。 可以隐藏你想要在两种方法中隐藏的变量：  
  
-   **通过范围进行隐藏。** 您可以通过范围隐藏变量包含你想要隐藏的变量的区域子区域内重新声明变量。  
  
-   **通过继承进行隐藏。** 如果在类级别定义你想要隐藏的变量，您可以隐藏它通过继承隐藏其与[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)派生类中的关键字。  
  
## <a name="two-ways-to-hide-a-variable"></a>若要隐藏的变量的两种方法  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>若要通过范围进行隐藏隐藏变量  
  
1.  确定定义你想要隐藏的变量的区域，并确定要重新定义它与您的变量在其中一个子区域。  
  
    |变量的区域|允许为重新定义它的子区域|  
    |-----------------------|-------------------------------------------|  
    |模块|该模块中的类|  
    |类|中的类的子类<br /><br /> 在类内的一个过程|  
  
     不能为例重新在该过程中，块中的过程变量定义中`If`...`End If`构造或`For`循环。  
  
2.  如果尚不存在，请创建子区域。  
  
3.  子区域，在编写[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)声明隐藏变量。  
  
     当子区域内的代码引用的变量名称时，编译器将解析为隐藏变量的引用。  
  
     下面的示例说明了通过作用域，以及一个引用，它会绕开隐藏进行隐藏。  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     前面的示例中声明变量`num`在模块级别和在过程级别 (在过程`show`)。 本地变量`num`隐藏模块级变量`num`内`show`，因此本地变量设置为 2。 但是，没有本地变量为卷影`num`在`useModuleLevelNum`过程。 因此，`useModuleLevelNum`模块级变量的值设置为 1。  
  
     `MsgBox`内调用`show`通过符合条件的可忽略隐藏机制`num`模块名称。 因此，它将显示而不是本地变量的模块级变量。  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>若要通过隐藏通过继承隐藏的变量  
  
1.  请确保你想要隐藏的变量声明在类中，并在类级别 （任何过程之外）。 否则不能通过继承隐藏它。  
  
2.  定义派生自变量的类，如果尚不存在的类。  
  
3.  在派生类中，编写`Dim`声明您的变量的语句。 包括[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)声明中的关键字。  
  
     当在派生类中的代码引用的变量名称时，编译器将解析到您的变量引用。  
  
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
 隐藏引入了多个版本具有相同名称的变量。 当代码语句引用的变量名称时，编译器将该引用解析的版本取决于代码语句的位置和限定字符串存在等因素。 这可能会增加被隐藏变量的意外版本中引用的风险。 通过完全限定对隐藏变量的所有引用，可以降低该风险。  
  
## <a name="see-also"></a>请参阅

- [对已声明元素的引用](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [在 Visual Basic 中隐藏](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [隐藏和重写之间的差异](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [如何：隐藏继承的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [如何：访问被派生类隐藏的变量](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase 和 MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [继承的基础知识](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
