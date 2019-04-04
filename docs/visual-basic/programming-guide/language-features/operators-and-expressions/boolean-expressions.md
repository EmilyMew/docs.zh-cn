---
title: 布尔表达式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: ce9146791935a488108d110134e9273507b0da6f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825529"
---
# <a name="boolean-expressions-visual-basic"></a>布尔表达式 (Visual Basic)
一个*布尔表达式*是表达式的计算结果为值[布尔数据类型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md):`True`或`False`。 `Boolean` 表达式可以采用多种形式。 简单的方法是直接的值的比较`Boolean`变量`Boolean`文本，如下面的示例中所示。  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>两种含义的 = 运算符  
 请注意，在赋值语句`newCustomer = True`与在前面的示例中，表达式看起来相同，但它执行不同的功能，以不同的方式使用。 在前面的示例中，表达式`newCustomer = True`表示一个布尔值，和`=`符号被解释为比较运算符。 在独立语句中，`=`符号被解释为赋值运算符，分配给左侧变量右侧值。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 有关详细信息，请参阅[值的比较](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)并[语句](../../../../visual-basic/language-reference/statements/index.md)。  
  
## <a name="comparison-operators"></a>比较运算符  
 比较运算符，如`=`， `<`， `>`， `<>`， `<=`，并`>=`通过比较运算符右侧表达式的左侧和右侧表达式产生布尔表达式运算符和评估结果作为`True`或`False`。 下面的示例阐释了这一点。  
  
 `42 < 81`  
  
 由于 42 是小于 81，前面示例中的布尔表达式计算结果为`True`。 此类表达式的详细信息，请参阅[值的比较](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)。  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>与逻辑运算符结合使用的比较运算符  
 可以使用逻辑运算符以生成更复杂的布尔表达式组合比较表达式。 下面的示例演示如何将具有一个逻辑运算符结合使用的比较运算符。  
  
 `x > y And x < 1000`  
  
 在前面的示例中，整个表达式的值取决于每侧的表达式的值`And`运算符。 如果两个表达式均`True`，则整个表达式的计算结果为`True`。 如果任一表达式`False`，则整个表达式的计算结果为`False`。  
  
## <a name="short-circuiting-operators"></a>短路运算符  
 逻辑运算符`AndAlso`并`OrElse`表现出行为称为*短路*。 短路运算符首先计算左的操作数。 如果左的操作数确定整个表达式的值，然后程序执行继续进行而不计算右侧表达式。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 在上述示例中，运算符将计算左侧的表达式`45 < 12`。 由于左侧的表达式的计算结果为`False`，整个逻辑表达式的计算结果必须为`False`。 程序执行因此将跳过执行中的代码`If`而无需计算右侧表达式块`testFunction(3)`。 此示例不会调用`testFunction()`因为左侧的表达式使整个表达式。  
  
 同样，如果左侧的表达式在逻辑表达式中使用`OrElse`计算结果为`True`，执行过程前进到下一行代码而无需计算右侧表达式，因为左侧的表达式已经证明整个表达式。  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>与非短路运算符的比较  
 与此相反，计算逻辑运算符的两端时逻辑运算符`And`和`Or`使用。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 前面的示例调用`testFunction()`即使左侧的表达式的计算结果为`False`。  
  
## <a name="parenthetical-expressions"></a>加括号的表达式  
 可以使用括号来控制的布尔表达式计算顺序。 首先计算由括号括起来的表达式。 多个层级的嵌套，优先将授予嵌套最深的表达式。 在括号内，评估会继续按照运算符优先级规则。 有关详细信息，请参阅[在 Visual Basic 中的运算符优先级](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的逻辑和位运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [值的比较](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [语句](../../../../visual-basic/programming-guide/language-features/statements.md)
- [比较运算符](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [运算符的有效组合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Visual Basic 中的运算符优先级](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Boolean 数据类型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
