---
title: 在 lambda 表达式中使用迭代变量可能会产生意外的结果
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 618fc88a2ca92ec911a3fbd82de580403d924430
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841090"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>在 lambda 表达式中使用迭代变量可能会产生意外的结果
Lambda 表达式中使用迭代变量可能会产生意外的结果。 相反，创建一个本地变量在循环内的，并将其分配的迭代变量的值。  
  
 在循环中声明的 lambda 表达式中使用循环迭代变量时，会出现此警告。 例如，下面的示例会导致出现的警告。  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 下面的示例显示了可能会出现意外的结果。  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 `For`循环创建的 lambda 表达式，其中每个循环迭代变量的值将返回一个数组`i`。 当 lambda 表达式的计算`For Each`循环中，你可能希望看到 0、 1、 2、 3 和 4 显示，连续的值`i`中`For`循环。 相反，您看到的最终值`i`显示了五次：  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 默认情况下，此消息是一个警告。 若要深入了解如何隐藏警告或将警告视为错误，请参阅 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **错误 ID:** BC42324  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   将迭代变量的值分配给本地变量，并在 lambda 表达式中使用本地变量。  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>请参阅

- [Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
