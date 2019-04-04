---
title: /= 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: d9d3fa021654d3be1b9d304beb83caa737660264
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813985"
---
# <a name="-operator-visual-basic"></a>/= 运算符 (Visual Basic)
将表达式的值的变量或属性的值除以并将浮点结果赋给变量或属性。  
  
## <a name="syntax"></a>语法  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 必需。 任何数值变量或属性。  
  
 `expression`  
 必需。 任何数值表达式。  
  
## <a name="remarks"></a>备注  
 在左侧和右侧的元素`/=`运算符可以是简单的标量变量、 属性或数组的元素。 变量或属性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `/=`运算符首先将变量或属性 （在运算符的左侧） 的值除以 （对运算符的右侧） 的表达式的值。 然后，该运算符将浮点运算的结果分配给变量或属性。  
  
 此语句将分配`Double`给变量或在左侧的属性的值。 如果`Option Strict`是`On`，`variableorproperty`必须是`Double`。 如果`Option Strict`是`Off`，Visual Basic 执行的隐式转换和分配结果值输出到`variableorproperty`，可以在运行时错误。 有关详细信息，请参阅[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)并[Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
## <a name="overloading"></a>重载  
 [/ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)可以是*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 重载`/`运算符会影响的行为`/=`运算符。 如果你的代码使用`/=`上类或结构的重载`/`，确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`/=`运算符将一个`Integer`变量的第二个和分配给第一个变量的商。  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>请参阅

- [/ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\= 运算符](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
