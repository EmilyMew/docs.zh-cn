---
title: 后期绑定重载决策不能应用于“<procedurename>”，因为访问实例是一个接口类型
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 7f2ae3bb0e7c09d966c53fb17b1cbe675dfce8b9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814050"
---
# <a name="latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a>后期绑定重载决策不能应用于\<过程名称 > 因为访问实例是一个接口类型
编译器尝试解析对重载的属性或过程中，但引用失败，因为参数的类型`Object`和引用对象具有一个接口的数据类型。 `Object`参数强制编译器将引用解析为后期绑定。  
  
 在这些情况下，编译器将通过实现类而不是通过基础接口的重载解析。 如果类重命名其中一个重载版本，则编译器将不考虑该版本是重载方法，因为其名称不同。 这反过来会导致编译器忽略重命名的版本时可能已正确的选择来解析引用。  
  
 **错误 ID:** BC30933  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   使用`CType`强制转换的参数从`Object`到你想要调用的重载的签名由指定的类型。  
  
     请注意，它无法帮助转换到基础接口的引用对象。 您必须强制转换来避免此错误的参数。  
  
## <a name="example"></a>示例  
 下面的示例演示如何调用一个已重载的`Sub`会在编译时导致此错误的过程。  
  
```  
Module m1  
    Interface i1  
        Sub s1(ByVal p1 As Integer)  
        Sub s1(ByVal p1 As Double)  
    End Interface  
    Class c1  
        Implements i1  
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1  
        End Sub  
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1  
        End Sub  
    End Class  
    Sub Main()  
        Dim refer As i1 = New c1  
        Dim o1 As Object = 3.1415  
        ' The following reference is INVALID and causes a compiler error.  
        refer.s1(o1)   
    End Sub  
End Module  
```  
  
 在前面的示例中，如果编译器允许在调用`s1`分辨率一样编写的将会通过类发生`c1`而不是接口`i1`。 这就意味着编译器不会考虑`s2`因为其名称为在不同`c1`，即使它是正确的选择，因为由定义`i1`。  
  
 可以通过更改为以下代码行的任何一调用来纠正此错误：  
  
```  
refer.s1(CType(o1, Integer))  
refer.s1(CType(o1, Double))  
```  
  
 每个前面几行代码显式强制转换`Object`变量`o1`的重载定义的参数类型之一。  
  
## <a name="see-also"></a>请参阅

- [过程重载](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [重载决策](../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)
- [CType 函数](../../../visual-basic/language-reference/functions/ctype-function.md)
