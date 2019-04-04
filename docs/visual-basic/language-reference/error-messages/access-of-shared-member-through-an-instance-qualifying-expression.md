---
title: 通过实例访问共享成员；将不计算限定表达式
ms.date: 07/20/2015
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
ms.openlocfilehash: 8e6ddab16c59d7ce95d96b377e3f372f6ebe5278
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843560"
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>通过实例访问共享成员；将不计算限定表达式
使用类或结构的实例变量访问`Shared`变量、 属性、 过程或在该类或结构中定义的事件。 如果使用实例变量访问类或结构，例如常量或枚举，或一个嵌套的类或结构的隐式共享的成员，也可能发生此警告。  
  
 共享某个成员的目的是创建仅该成员的一个副本并使该单个副本可供类或结构声明它的每个实例。 为此目的，若要访问与一致`Shared`成员通过其类或结构的名称而不是包含的单独实例，该类或结构的变量。  
  
 访问`Shared`通过实例变量的成员可以使代码更难以理解通过隐藏该成员是这一事实`Shared`。 此外，如果此类访问是表达式的一部分执行其他操作，如`Function`返回的共享成员实例的过程，Visual Basic 将忽略表达式以及它将执行的任何其他操作。  
  
 有关详细信息和示例，请参阅[共享](../../../visual-basic/language-reference/modifiers/shared.md)。  
  
 默认情况下，此消息是一个警告。 若要深入了解如何隐藏警告或将警告视为错误，请参阅 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC42025  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   使用类或结构，它定义的名称`Shared`成员来访问它，如下面的示例中所示。  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  当两个编程元素具有相同名称时，警报是作用域的影响。 在上一示例中，如果通过使用声明的实例`Dim testClass as testClass = Nothing`，则编译器将调用`testClass.sayHello()`发生时通过类名，并不会出现警告的方法的访问。  
  
## <a name="see-also"></a>请参阅

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [在 Visual Basic 中的作用域](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
