---
title: 如何：控制变量 (Visual Basic 中) 的作用域
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: ef7957a991718112fe01c4fa3a85f29b9226abd3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818718"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>如何：控制变量 (Visual Basic 中) 的作用域
通常情况下，变量位于*作用域*，或作为参考，整个声明它的区域可见。 在某些情况下，该变量的*访问级别*可能会影响其作用域。  
  
 有关详细信息，请参阅 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
## <a name="scope-at-block-or-procedure-level"></a>在块或过程级别的作用域  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>若要使变量仅在一个块中可见  
  
-   位置[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)变量之间的起始和终止声明语句的该块中，例如之间`For`并`Next`语句的`For`循环。  
  
     您可以引用该变量只能在块中。  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>若要使变量仅在一个过程中可见  
  
-   位置`Dim`在过程内但在任何块外部变量的语句 (如`With`...`End With`块)。  
  
     您可以参考中的过程，包括在过程中包含的所有块内仅从变量。  
  
## <a name="scope-at-module-or-namespace-level"></a>在模块或 Namespace 级别的作用域  
 为方便起见，单个字词*模块级别*同样适用于模块、 类和结构。 模块级变量的访问级别确定其作用域。 包含模块、 类或结构的命名空间还会影响作用域。  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>若要使变量在整个模块、 类或结构可见  
  
1.  位置`Dim`内部模块、 类或结构，但在任何过程外部变量的语句。  
  
2.  包括[私有](../../../../visual-basic/language-reference/modifiers/private.md)中的关键字`Dim`语句。  
  
3.  您可以参考中的变量中的模块、 类或结构的任意位置，但不能从其外部。  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>若要使变量在整个命名空间内可见  
  
1.  位置`Dim`内部模块、 类或结构，但在任何过程外部变量的语句。  
  
2.  包括[友元](../../../../visual-basic/language-reference/modifiers/friend.md)或[公共](../../../../visual-basic/language-reference/modifiers/public.md)中的关键字`Dim`语句。  
  
3.  可以引用从任何位置的变量中包含模块、 类或结构的命名空间。  
  
## <a name="example"></a>示例  
 以下示例声明在模块级别的变量，并限制其对模块中的代码的可见性。  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 在前面的示例中，在模块中定义的所有过程`demonstrateScope`可以指`String`变量`strMsg`。 当`usePrivateVariable`调用过程，它显示的字符串变量内容`strMsg`对话框框中。  
  
 与前面的示例中，字符串变量进行如下更改`strMsg`可以由其声明的命名空间中的任意位置的代码引用。  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>可靠编程  
 变量，减少了必须为意外引用它来替换具有相同名称的另一个变量的范围越窄。 此外可以尽量减少引用匹配的问题。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 变量的范围越窄，它使用恶意代码可以进行不正确的较小的可能性。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的作用域](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [在 Visual Basic 中的生存期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [在 Visual Basic 中的访问级别](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [变量](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [变量声明](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)
