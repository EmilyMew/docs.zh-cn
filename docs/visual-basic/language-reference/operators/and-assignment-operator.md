---
title: '&amp;= 运算符 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: a79e779d8fcf549daeabc494e0a55deee30b5d22
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835461"
---
# <a name="amp-operator-visual-basic"></a>&amp;= 运算符 (Visual Basic)
将连接在一起`String`表达式`String`变量或属性，并将结果赋给变量或属性。  
  
## <a name="syntax"></a>语法  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 必需。 任何`String`变量或属性。  
  
 `expression`  
 必需。 任何 `String` 表达式。  
  
## <a name="remarks"></a>备注  
 在左侧和右侧的元素`&=`运算符可以是简单的标量变量、 属性或数组的元素。 变量或属性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。 `&=`运算符串联`String`到其右侧的表达式`String`变量或属性在其左侧，并将结果赋给变量或在其左侧的属性。  
  
## <a name="overloading"></a>重载  
 [& 运算符](../../../visual-basic/language-reference/operators/concatenation-operator.md)可以是*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 重载`&`运算符会影响的行为`&=`运算符。 如果你的代码使用`&=`上类或结构的重载`&`，确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`&=`运算符来串联两个`String`变量并将结果赋给第一个变量。  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>请参阅

- [& 运算符](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+= 运算符](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [串联运算符](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
