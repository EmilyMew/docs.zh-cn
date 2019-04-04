---
title: += 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 4b8f36397d0f52866ebe9fa188d6b163364aeffc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838990"
---
# <a name="-operator-visual-basic"></a>+= 运算符 (Visual Basic)
将数值表达式的值添加到的数值变量或属性的值并将结果赋给变量或属性。 此外可用于串联`String`表达式`String`变量或属性，并且将结果赋给变量或属性。  
  
## <a name="syntax"></a>语法  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 必需。 任何数字或`String`变量或属性。  
  
 `expression`  
 必需。 任何数字或`String`表达式。  
  
## <a name="remarks"></a>备注  
 在左侧和右侧的元素`+=`运算符可以是简单的标量变量、 属性或数组的元素。 变量或属性不能[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)。  
  
 `+=`运算符将值添加到变量或属性在其左侧，其右侧，并将结果赋给变量或在其左侧的属性。 `+=`运算符还可用于连接`String`到其右侧的表达式`String`变量或在其左侧，并将结果赋给变量的属性或在其左侧的属性。  
  
> [!NOTE]
>  当你使用`+=`运算符，您可能不能确定是否将进行加法或字符串串联。 使用`&=`串联以消除二义性，并提供自我说明代码的运算符。  
  
 此赋值运算符隐式执行扩大转换而不是收缩转换，如果编译环境强制实施严格的语义。 这些转换的详细信息，请参阅[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。 有关严格和宽松的语义的详细信息，请参阅[Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
 如果允许宽松的语义，`+=`运算符隐式执行各种字符串和数字转换执行的相同`+`运算符。 这些转换的详细信息，请参阅[+ 运算符](../../../visual-basic/language-reference/operators/addition-operator.md)。  
  
## <a name="overloading"></a>重载  
 `+`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 重载`+`运算符会影响的行为`+=`运算符。 如果你的代码使用`+=`上类或结构的重载`+`，确保了解其重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例使用`+=`运算符将一个变量的值与另一个组合在一起。 第一部分使用`+=`与数值变量添加到另一个值。 第二部分使用`+=`与`String`变量，以连接与另一个值。 在这两种情况下，结果被分配给第一个变量。  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 值`num1`13 和的值现在是`str1`现在是"103"。  
  
## <a name="see-also"></a>请参阅

- [+ 运算符](../../../visual-basic/language-reference/operators/addition-operator.md)
- [赋值运算符](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [串联运算符](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
