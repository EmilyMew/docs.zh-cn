---
title: '\= 运算符 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 377a14a76f67e938f24c973b5946abd63f851bfd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842533"
---
# <a name="-operator"></a>\\= 运算符
将表达式的值的变量或属性的值除以并将整数结果赋给变量或属性。  
  
## <a name="syntax"></a>语法  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 必需。 任何数值变量或属性。  
  
 `expression`  
 必需。 任何数值表达式。  
  
## <a name="remarks"></a>备注  
 在左侧和右侧的元素`\=`运算符可以是简单的标量变量、 属性或数组的元素。 变量或属性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `\=`运算符将在其右侧的值的变量或在其左侧的属性值除以并将整数结果赋给变量或在其左侧的属性  
  
 整数除法的详细信息，请参阅[\ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)。  
  
## <a name="overloading"></a>重载  
 `\`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 重载`\`运算符会影响的行为`\=`运算符。 如果你的代码使用`\=`上类或结构的重载`\`，确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`\=`运算符将一个`Integer`通过第二个和整数结果到第一个变量分配变量。  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>请参阅

- [\ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [/ = 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
