---
title: AndAlso 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 3876fd9c32d486b8ebecc9ee2428486a687a1624
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817118"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso 运算符 (Visual Basic)
执行短路逻辑与运算，对两个表达式。  
  
## <a name="syntax"></a>语法  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`result`|必需。 任何 `Boolean` 表达式。 结果是`Boolean`比较两个表达式的结果。|  
|`expression1`|必需。 任何 `Boolean` 表达式。|  
|`expression2`|必需。 任何 `Boolean` 表达式。|  
  
## <a name="remarks"></a>备注  
 逻辑操作称为*短路*如果已编译的代码可以跳过一个具体取决于另一个表达式的结果表达式的计算。 如果计算的第一个表达式的结果确定该操作的最终结果，则无需评估的第二个表达式，因为它不能更改最终结果。 如果跳过的表达式很复杂，或如果它涉及过程调用，则短路可以提高性能。  
  
 如果这两个表达式的计算结果为`True`，`result`是`True`。 下表说明了如何`result`确定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|（不会评估）|`False`|  
  
## <a name="data-types"></a>数据类型  
 `AndAlso`仅对定义运算符[布尔数据类型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)。 Visual Basic 将根据需要向每个操作数`Boolean`，并执行全部操作`Boolean`。 如果将结果分配到数值类型，Visual Basic 会将其转换从`Boolean`为该类型。 这可能产生意外的行为。 例如，`5 AndAlso 12`会导致`–1`转换为`Integer`。  
  
## <a name="overloading"></a>重载  
 [And 运算符](../../../visual-basic/language-reference/operators/and-operator.md)并[IsFalse 运算符](../../../visual-basic/language-reference/operators/isfalse-operator.md)可以是*重载*，这意味着，类或结构可以重新定义其行为时，操作数的类型，类或结构。 重载`And`并`IsFalse`运算符影响的行为`AndAlso`运算符。 如果你的代码使用`AndAlso`上类或结构的重载`And`和`IsFalse`，确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`AndAlso`运算符对两个表达式执行逻辑与运算。 结果是`Boolean`值，该值表示是否整个联合表达式为 true。 如果第一个表达式是`False`，则不计算第二个。  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 前面的示例生成的结果`True`， `False`，和`False`分别。 中的计算`secondCheck`，因为第一个已不会计算第二个表达式`False`。 但是，第二个表达式计算的计算中`thirdCheck`。  
  
## <a name="example"></a>示例  
 下面的示例演示`Function`搜索给定值的数组元素中的过程。 如果数组为空，或已超过数组长度，`While`语句不会测试针对搜索值的数组元素。  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>请参阅

- [逻辑/按位运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And 运算符](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse 运算符](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
