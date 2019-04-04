---
title: ^= 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5d7b3dcb55192167512e0934e09cff7dfddb6d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819642"
---
# <a name="-operator-visual-basic"></a>^= 运算符 (Visual Basic)
引发的变量或表达式的属性的值，并将结果赋回给变量或属性。  
  
## <a name="syntax"></a>语法  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 必需。 任何数值变量或属性。  
  
 `expression`  
 必需。 任何数值表达式。  
  
## <a name="remarks"></a>备注  
 在左侧和右侧的元素`^=`运算符可以是简单的标量变量、 属性或数组的元素。 变量或属性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `^=`运算符首先引发变量或属性 （在运算符的左侧） 的值 （在运算符的右侧） 的表达式的值的幂。 然后，该运算符将该操作的结果赋回给变量或属性。  
  
 Visual Basic 始终执行中的求幂[双精度数据类型](../../../visual-basic/language-reference/data-types/double-data-type.md)。 任何其他类型的操作数将转换为`Double`，结果始终为`Double`。  
  
 值`expression`可以是小数，负号，或两者。  
  
## <a name="overloading"></a>重载  
 [^ 运算符](../../../visual-basic/language-reference/operators/exponentiation-operator.md)可以是*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 重载`^`运算符会影响的行为`^=`运算符。 如果你的代码使用`^=`上类或结构的重载`^`，确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`^=`运算符的一个值进行`Integer`变量的第二个变量中，并将结果赋给第一个变量。  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>请参阅

- [^ 运算符](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
