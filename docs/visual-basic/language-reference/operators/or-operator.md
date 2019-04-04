---
title: Or 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835292"
---
# <a name="or-operator-visual-basic"></a>Or 运算符 (Visual Basic)
对两个执行逻辑或运算`Boolean`表达式或按位析取两个数值表达式。  
  
## <a name="syntax"></a>语法  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>部件  
 `result`  
 必需。 任何`Boolean`或数值表达式。 有关`Boolean`比较，`result`是两个包含的逻辑析取`Boolean`值。 对于按位运算`result`是一个数值表示包含按位析取的两个数值位模式。  
  
 `expression1`  
 必需。 任何`Boolean`或数值表达式。  
  
 `expression2`  
 必需。 任何`Boolean`或数值表达式。  
  
## <a name="remarks"></a>备注  
 有关`Boolean`比较，`result`是`False`当且仅当`expression1`并`expression2`的计算结果为`False`。 下表说明了如何`result`确定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  在中`Boolean`比较，`Or`运算符始终计算这两个表达式，它可能包含使过程调用。 [OrElse 运算符](../../../visual-basic/language-reference/operators/orelse-operator.md)执行*短路*，这意味着，如果`expression1`是`True`，然后`expression2`则不会评估。  
  
 对于按位运算`Or`运算符中两个数值表达式执行位置相同的位的按位比较，并设置相应的位中`result`根据下表。  
  
|如果位`expression1`是|和中位`expression2`是|中的位`result`是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  由于逻辑和位运算符优先级低于其他算术和关系运算符，则任何按位运算应括在括号中以确保准确的执行。  
  
## <a name="data-types"></a>数据类型  
 如果操作数包括一个`Boolean`Visual Basic 表达式和一个数值表达式，将转换`Boolean`为数字值的表达式 (– 1 表示`True`，使用 0 表示`False`)，并执行按位运算。  
  
 有关`Boolean`比较，结果的数据类型是`Boolean`。 有关按位比较，结果数据类型为适用于的数据类型的数值类型`expression1`和`expression2`。 请参阅中的"关系与按位比较"表[数据类型的运算符结果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
## <a name="overloading"></a>重载  
 `Or`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`Or`运算符对两个表达式执行逻辑或运算。 结果是`Boolean`值，该值表示两个表达式之一是否`True`。  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 前面的示例生成的结果`True`， `True`，和`False`分别。  
  
## <a name="example"></a>示例  
 下面的示例使用`Or`运算符对两个数值表达式的单个位执行逻辑或运算。 如果任一操作数中的相应位设置为 1，在结果模式位被设置。  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 前面的示例分别生成 10、 14 和 14 的结果。  
  
## <a name="see-also"></a>请参阅

- [逻辑/按位运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse 运算符](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
