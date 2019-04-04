---
title: And 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 7e25f25677fa684427bdaf00cea73916ffbad655
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818613"
---
# <a name="and-operator-visual-basic"></a>And 运算符 (Visual Basic)
对两个执行逻辑与运算`Boolean`表达式或对两个数值表达式位与运算。  
  
## <a name="syntax"></a>语法  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>部件  
 `result`  
 必需。 任何`Boolean`或数值表达式。 对于布尔比较`result`是两个逻辑与运算`Boolean`值。 对于按位运算`result`是数字值表示两个数值位模式位与运算。  
  
 `expression1`  
 必需。 任何`Boolean`或数值表达式。  
  
 `expression2`  
 必需。 任何`Boolean`或数值表达式。  
  
## <a name="remarks"></a>备注  
 对于布尔比较`result`是`True`当且仅当`expression1`并`expression2`的计算结果为`True`。 下表说明了如何`result`确定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  在布尔比较中，`And`运算符始终计算这两个表达式，它可能包含使过程调用。 [AndAlso 运算符](../../../visual-basic/language-reference/operators/andalso-operator.md)执行*短路*，这意味着，如果`expression1`是`False`，然后`expression2`则不会评估。  
  
 当应用于数字值时`And`运算符中两个数值表达式执行位置相同的位的按位比较，并设置相应的位中`result`根据下表。  
  
|如果位`expression1`是|和中位`expression2`是|中的位`result`是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  由于逻辑和位运算符优先级低于其他算术和关系运算符，则任何按位运算应括在括号中以确保准确的结果。  
  
## <a name="data-types"></a>数据类型  
 如果操作数包括一个`Boolean`Visual Basic 表达式和一个数值表达式，将转换`Boolean`为数字值的表达式 (– 1 表示`True`，使用 0 表示`False`)，并执行按位运算。  
  
 对于布尔比较，结果的数据类型是`Boolean`。 有关按位比较，结果数据类型为适用于的数据类型的数值类型`expression1`和`expression2`。 请参阅中的"关系与按位比较"表[数据类型的运算符结果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
> [!NOTE]
>  `And`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`And`运算符对两个表达式执行逻辑与运算。 结果是`Boolean`值，该值表示两个表达式是否`True`。  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 前面的示例生成的结果`True`和`False`分别。  
  
## <a name="example"></a>示例  
 下面的示例使用`And`运算符对两个数值表达式的单个位执行逻辑与运算。 如果操作数中的相应位均为这两个设置为 1，在结果模式位被设置。  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 前面的示例分别生成 8、 2 和 0，的结果。  
  
## <a name="see-also"></a>请参阅

- [逻辑/按位运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso 运算符](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
