---
title: 异或运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 0cba3a995fb1ab774c8a5308e58f0b6905fc23f3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827063"
---
# <a name="xor-operator-visual-basic"></a>异或运算符 (Visual Basic)
执行逻辑异或对两个`Boolean`表达式或对两个数值表达式按位异运算。  
  
## <a name="syntax"></a>语法  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>部件  
 `result`  
 必需。 任何`Boolean`或数值变量。 对于布尔比较`result`是两个逻辑异运算 （排他逻辑析取）`Boolean`值。 对于按位运算`result`是数字值，该值表示两个数值位模式的按位异 （排他的按位析取）。  
  
 `expression1`  
 必需。 任何`Boolean`或数值表达式。  
  
 `expression2`  
 必需。 任何`Boolean`或数值表达式。  
  
## <a name="remarks"></a>备注  
 对于布尔比较`result`是`True`当且仅当之一`expression1`和`expression2`计算结果为`True`。 也就是说，当且仅当`expression1`并`expression2`评估为相反`Boolean`值。 下表说明了如何`result`确定。  
  
|如果`expression1`是|和`expression2`是|值`result`是|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  在布尔比较中，`Xor`运算符始终计算这两个表达式，它可能包含使过程调用。 没有任何短路`Xor`，因为结果始终取决于两个操作数。 有关*短路*逻辑运算符，请参阅[AndAlso 运算符](../../../visual-basic/language-reference/operators/andalso-operator.md)并[OrElse 运算符](../../../visual-basic/language-reference/operators/orelse-operator.md)。  
  
 对于按位运算`Xor`运算符中两个数值表达式执行位置相同的位的按位比较，并设置相应的位中`result`根据下表。  
  
|如果位`expression1`是|和中位`expression2`是|中的位`result`是|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  由于逻辑和位运算符优先级低于其他算术和关系运算符，则任何按位运算应括在括号中以确保准确的执行。  
  
 例如，5 `Xor` 3 为 6。 若要查看其中的原因，将 5 和 3 转换为其二进制表示形式、 101 和 011。 然后使用上表来确定 101 Xor 011 是为 110 时，即十进制数 6 的二进制表示形式。  
  
## <a name="data-types"></a>数据类型  
 如果操作数包括一个`Boolean`Visual Basic 表达式和一个数值表达式，将转换`Boolean`为数字值的表达式 (– 1 表示`True`，使用 0 表示`False`)，并执行按位运算。  
  
 有关`Boolean`比较，结果的数据类型是`Boolean`。 有关按位比较，结果数据类型为适用于的数据类型的数值类型`expression1`和`expression2`。 请参阅中的"关系与按位比较"表[数据类型的运算符结果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。  
  
## <a name="overloading"></a>重载  
 `Xor`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`Xor`运算符对两个表达式执行逻辑异运算 （互斥逻辑析）。 结果是`Boolean`值，该值表示是否恰好有一个表达式是`True`。  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 前面的示例生成的结果`False`， `True`，和`False`分别。  
  
## <a name="example"></a>示例  
 下面的示例使用`Xor`运算符对两个数值表达式的单个位执行逻辑异运算 （互斥逻辑析）。 在结果模式位设置如果恰好有一个操作数中的相应位设置为 1。  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 前面的示例分别生成 2，12 和 14 的结果。  
  
## <a name="see-also"></a>请参阅

- [逻辑/按位运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
