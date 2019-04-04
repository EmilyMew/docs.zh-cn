---
title: 值的比较 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 270b226d0a1aa7d08721e6f9ed36d68492685af3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818600"
---
# <a name="value-comparisons-visual-basic"></a>值的比较 (Visual Basic)
比较运算符可以用于构造比较数值变量的值的表达式。 两个表达式返回`Boolean`值根据比较是 true 或 false。 此类表达式的示例如下所示。  
  
 `45 > 26`  
  
 `26 > 45`  
  
 第一个表达式的计算结果为`True`，这是因为 45 大于 26。 第二个示例的计算结果为`False`，这是因为 26 不超过 45。  
  
 此外可以比较这种方式中的数值表达式。 要比较的表达式本身可以是复杂表达式，如以下示例所示。  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 在前面的复杂表达式包括文本、 变量和函数调用。 比较运算符两侧的表达式计算，，然后使用比较结果值`>=`比较运算符。 如果左侧和右侧表达式的值是否大于或等于右侧表达式的值，整个表达式的计算结果`True`; 否则为为其计算结果为`False`。  
  
 比较值的表达式最常用于`If...Then`构造，如以下示例所示。  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=`符号是比较运算符和赋值运算符。 当用作比较运算符，它计算左侧的值是否等于右侧的值，如下面的示例中所示。  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 此外可以任意位置使用比较表达式`Boolean`值是所需，例如，在`If`， `While`， `Loop`，或`ElseIf`语句中，或者当将分配到或将值传递给`Boolean`变量。 在以下示例中，通过比较表达式返回的值分配给`Boolean`变量。  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>请参阅

- [布尔表达式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [运算符和表达式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [在 Visual Basic 中的比较运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [如何：计算数值](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic 中的运算符优先级](../../../../visual-basic/language-reference/operators/operator-precedence.md)
