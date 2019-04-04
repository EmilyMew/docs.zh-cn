---
title: 无法推断出变量“<variablename>”的类型，因为它绑定到封闭范围中的某个字段
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: bcd142785d8ee736c6a1b41950fae80e4d26fa18
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838805"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a>变量的类型\<变量名 >' 绑定到封闭范围中的字段，因此将不会推断
变量的类型\<变量名 >' 绑定到封闭范围中的字段，因此将不会推断。 请更改名称\<变量名 >，或使用完全限定的名称 （例如，Me.variablename 或 MyBase.variablename）。  
  
 在代码中的循环控制变量与类或其他封闭范围内的字段具有相同的名称。 因为控制变量用在无需`As`子句，它绑定到封闭范围中的字段和编译器不为其创建一个新的变量或推断出类型。  
  
 在以下示例中，`Index`中的控制变量`For`语句中，绑定到`Index`字段中`Customer`类。 编译器不会创建新的变量控制变量`Index`或推断其类型。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 默认情况下，此消息是一个警告。 有关如何隐藏警告或如何将警告视为错误的信息，请参见 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC42110  
  
### <a name="to-address-this-warning"></a>解决此警告  
  
-   通过其名称更改为标识符，也不是类的字段的名称使本地循环控制变量。  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   阐明循环控制变量绑定到类字段，通过前缀来`Me.`向变量名称。  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   使用而不是依赖于本地类型推断，`As`子句来指定 for 循环控制变量的类型。  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a>示例  
 下面的代码演示在位置中的第一个更正与前面的示例。  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>请参阅

- [Option Infer 语句](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [For Each...Next 语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [如何：引用对象的当前实例](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Me、My、MyBase 和 MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
