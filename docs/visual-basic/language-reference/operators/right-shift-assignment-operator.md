---
title: '>>= 运算符 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 1076ce62077391f2c88ebdd621d1dbd6fb40d647
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838958"
---
# <a name="-operator-visual-basic"></a>>> = 运算符 (Visual Basic)
对变量或属性的值执行算术右移位运算并将结果赋回给变量或属性。  
  
## <a name="syntax"></a>语法  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 必需。 变量或属性的一种整型类型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`)。  
  
 `amount`  
 必需。 数值表达式的数据类型扩大到`Integer`。  
  
## <a name="remarks"></a>备注  
 在左侧和右侧的元素`>>=`运算符可以是简单的标量变量、 属性或数组的元素。 变量或属性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `>>=`运算符首先对变量或属性的值执行算术右移位运算。 然后，该运算符将该操作的结果赋回给变量或属性。  
  
 算术移位不是循环，这意味着移出结果的一端的数位另一端不重新移入。 在算术右移位运算移出最右侧位位置的位将被丢弃，并最左边的位传播到左侧而空出的位位置。 这意味着，如果`variableorproperty`为负值，空出的位置将设置为一。 如果`variableorproperty`为正，或者如果其数据类型为无符号的类型，空出的位置被设置为零。  
  
## <a name="overloading"></a>重载  
 [>> 运算符](../../../visual-basic/language-reference/operators/right-shift-operator.md)可以是*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 重载`>>`运算符会影响的行为`>>=`运算符。 如果你的代码使用`>>=`上类或结构的重载`>>`，确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`>>=`运算符将该位模式移位的`Integer`变量直接由指定的量和将结果赋给变量。  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>请参阅

- [>> 运算符](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [移位运算符](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
