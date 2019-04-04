---
title: Not 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 4e54fdca9123ad5595eb9a8c5e2ac5bc303a8f6a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824195"
---
# <a name="not-operator-visual-basic"></a>Not 运算符 (Visual Basic)
对执行逻辑非运算`Boolean`表达式或对数值表达式的按位求反运算。  
  
## <a name="syntax"></a>语法  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>部件  
 `result`  
 必需。 任何`Boolean`或数值表达式。  
  
 `expression`  
 必需。 任何`Boolean`或数值表达式。  
  
## <a name="remarks"></a>备注  
 有关`Boolean`表达式下, 表说明了如何`result`确定。  
  
|如果`expression`是|值`result`是|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 对于数值表达式，`Not`运算符反转任何数值表达式的位值，并设置相应的位中`result`根据下表。  
  
|如果位`expression`是|中的位`result`是|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  由于逻辑和位运算符优先级低于其他算术和关系运算符，则任何按位运算应括在括号中以确保准确的执行。  
  
## <a name="data-types"></a>数据类型  
 对于布尔求反，结果的数据类型是`Boolean`。 对于按位求反，结果数据类型是相同的`expression`。 但是，如果表达式为`Decimal`，结果是`Long`。  
  
## <a name="overloading"></a>重载  
 `Not`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，其操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`Not`运算符执行逻辑求反`Boolean`表达式。 结果是`Boolean`值，该值表示表达式的值相反。  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 前面的示例生成的结果`False`和`True`分别。  
  
## <a name="example"></a>示例  
 下面的示例使用`Not`运算符执行逻辑求反运算的数值表达式的单个位。 在结果模式位设置为包括符号位的操作数模式中的对应位相反。  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 前面的示例分别生成-11-9，-7 的结果。  
  
## <a name="see-also"></a>请参阅

- [逻辑/按位运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
