---
title: '*= 运算符 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 7c009a6b3acfe1528a2c34ed1e10735ac86507e6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839309"
---
# <a name="-operator-visual-basic"></a>*= 运算符 (Visual Basic)
将表达式的值的变量或属性的值相乘并将结果赋给变量或属性。  
  
## <a name="syntax"></a>语法  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 必需。 任何数值变量或属性。  
  
 `expression`  
 必需。 任何数值表达式。  
  
## <a name="remarks"></a>备注  
 在左侧和右侧的元素`*=`运算符可以是简单的标量变量、 属性或数组的元素。 变量或属性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `*=`运算符首先用变量或属性 （在运算符的左侧） 的值乘以 （运算符右侧） 的表达式的值。 然后，运算符将该操作的结果分配给变量或属性。  
  
## <a name="overloading"></a>重载  
 [* 运算符](../../../visual-basic/language-reference/operators/multiplication-operator.md)可以是*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 重载`*`运算符会影响的行为`*=`运算符。 如果你的代码使用`*=`上类或结构的重载`*`，确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`*=`运算符将一个`Integer`变量通过第二个并将结果赋给第一个变量。  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>请参阅

- [* 运算符](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
