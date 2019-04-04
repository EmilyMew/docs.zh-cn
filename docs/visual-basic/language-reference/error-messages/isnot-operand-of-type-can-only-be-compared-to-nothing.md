---
title: 类型“typename”的操作数“IsNot”只能与“Nothing”比较，因为“typename”是一个可以为 null 的类型
ms.date: 07/20/2015
f1_keywords:
- bc32128
- vbc32128
helpviewer_keywords:
- BC32128
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
ms.openlocfilehash: be2a3239b2ca520c4051a1504f91a766b4401a05
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834018"
---
# <a name="isnot-operand-of-type-typename-can-only-be-compared-to-nothing-because-typename-is-a-nullable-type"></a>类型“typename”的操作数“IsNot”只能与“Nothing”比较，因为“typename”是一个可以为 null 的类型
声明为可以为 null 的变量进行了比较表达式以外`Nothing`使用`IsNot`运算符。  
  
 **错误 ID:** BC32128  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
1.  要将可以为 null 的类型和表达式进行比较（而不是使用 `Nothing` 运算符比较 `IsNot` ），请调用可以为 null 的类型中的 `GetType` 方法并将结果与表达式进行比较，如下面的示例所示。  
  
```vb  
Dim number? As Integer = 5  
  
If number IsNot Nothing Then  
  If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
  End If  
End If  
```  
  
## <a name="see-also"></a>请参阅

- [可以为 null 的值类型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [IsNot 运算符](../../../visual-basic/language-reference/operators/isnot-operator.md)
