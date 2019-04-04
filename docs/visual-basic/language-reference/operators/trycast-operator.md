---
title: TryCast 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: c0eea4565d5040bb00743fc7864ac15b0fccdea9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831587"
---
# <a name="trycast-operator-visual-basic"></a>TryCast 运算符 (Visual Basic)
引入了不会引发异常的类型转换运算。  
  
## <a name="remarks"></a>备注  
 如果尝试执行的转换失败，`CType`并`DirectCast`同时引发<xref:System.InvalidCastException>错误。 这会产生负面影响应用程序的性能。 `TryCast` 返回[Nothing](../../../visual-basic/language-reference/nothing.md)，以便无需处理可能的异常，只需测试针对返回的结果`Nothing`。  
  
 您使用`TryCast`关键字使用的相同方式[CType Function](../../../visual-basic/language-reference/functions/ctype-function.md)并且[DirectCast 运算符](../../../visual-basic/language-reference/operators/directcast-operator.md)关键字。 提供作为第一个参数，并将其转换为作为第二个参数的类型的表达式。 `TryCast` 只对引用类型，如类和接口执行操作。 它需要两个类型之间的继承或实现关系。 这意味着，必须继承自或实现另一种类型。  
  
## <a name="errors-and-failures"></a>错误和失败  
 `TryCast` 如果它检测到任何继承或实现关系不存在，将生成编译器错误。 但缺少的编译器错误不会保证成功转换。 如果所需的转换收缩转换，它可能在运行时失败。 如果发生这种情况，`TryCast`将返回[Nothing](../../../visual-basic/language-reference/nothing.md)。  
  
## <a name="conversion-keywords"></a>转换关键字  
 类型转换关键字的比较是按如下所示。  
  
|关键字|数据类型|自变量的关系|运行时失败|  
|---|---|---|---|  
|[CType 函数](../../../visual-basic/language-reference/functions/ctype-function.md)|任何数据类型|必须在两个数据类型之间定义扩大或收缩转换|将引发 <xref:System.InvalidCastException>|  
|[DirectCast 运算符](../../../visual-basic/language-reference/operators/directcast-operator.md)|任何数据类型|一种类型必须继承自或实现另一个类型|将引发 <xref:System.InvalidCastException>|  
|`TryCast`|仅适用于引用类型|一种类型必须继承自或实现另一个类型|返回[执行任何操作](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>示例  
 下面的示例说明如何使用 `TryCast`。  
  
 [!code-vb[VbVbalrKeywords#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>请参阅

- [扩大转换和收缩转换](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [隐式转换和显式转换](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
