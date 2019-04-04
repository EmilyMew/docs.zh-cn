---
title: DirectCast 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 628ce4f06b91d0f514f71dea3aad8ea0fee6dccf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821499"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast 运算符 (Visual Basic)
引入了基于继承或实现的类型转换运算。  
  
## <a name="remarks"></a>备注  
 `DirectCast` 不使用 Visual Basic 运行时帮助器例程进行转换，以便它可以提供某种程度上更好的性能比`CType`时从数据类型进行来回转换`Object`。  
  
 您使用`DirectCast`关键字类似于您使用的方式[CType Function](../../../visual-basic/language-reference/functions/ctype-function.md)并且[TryCast 运算符](../../../visual-basic/language-reference/operators/trycast-operator.md)关键字。 提供作为第一个参数，并将其转换为作为第二个参数的类型的表达式。 `DirectCast` 需要两个参数的数据类型之间的继承或实现关系。 这意味着，必须继承自或实现另一种类型。  
  
## <a name="errors-and-failures"></a>错误和失败  
 `DirectCast` 如果它检测到任何继承或实现关系不存在，将生成编译器错误。 但缺少的编译器错误不会保证成功转换。 如果所需的转换收缩转换，它可能在运行时失败。 如果发生这种情况，则运行时会引发<xref:System.InvalidCastException>错误。  
  
## <a name="conversion-keywords"></a>转换关键字  
 类型转换关键字的比较是按如下所示。  
  
|关键字|数据类型|自变量的关系|运行时失败|  
|---|---|---|---|  
|[CType 函数](../../../visual-basic/language-reference/functions/ctype-function.md)|任何数据类型|必须在两个数据类型之间定义扩大或收缩转换|将引发 <xref:System.InvalidCastException>|  
|`DirectCast`|任何数据类型|一种类型必须继承自或实现另一个类型|将引发 <xref:System.InvalidCastException>|  
|[TryCast 运算符](../../../visual-basic/language-reference/operators/trycast-operator.md)|仅适用于引用类型|一种类型必须继承自或实现另一个类型|返回[执行任何操作](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>示例  
 下面的示例演示的两种用法`DirectCast`，一个在运行的时，另一个失败的成功。  
  
 [!code-vb[VbVbalrKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#1)]  
  
 在前面的示例中，运行时类型`q`是`Double`。 `CType` 会成功，因为`Double`可转换为`Integer`。 但是，第一个`DirectCast`在运行时失败，因为运行时类型的`Double`具有不到具有继承关系`Integer`，即使已存在的转换。 第二个`DirectCast`成功，因为它将从类型转换<xref:System.Windows.Forms.Form>键入<xref:System.Windows.Forms.Control>，从其<xref:System.Windows.Forms.Form>继承。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>
- [扩大转换和收缩转换](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隐式转换和显式转换](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
