---
title: 运算符的有效组合 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841235"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>运算符的有效组合 (Visual Basic)
复杂表达式可以包含许多不同的运算符。 下面的示例阐释了这一点。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 创建复杂表达式，例如前面示例中需要全面了解运算符优先级规则。 有关详细信息，请参阅[在 Visual Basic 中的运算符优先级](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="parenthetical-expressions"></a>加括号的表达式  
 通常，你希望以不同顺序由运算符优先级确定来执行的操作。 请看下面的示例。  
  
 `x = z * y + 4`  
  
 前面的示例将相乘`z`由`y`，然后将结果与`4`。 但是，如果你想要添加`y`并`4`相乘的结果之前`z`，可以使用括号来覆盖正常运算符优先级。 通过表达式括在括号中，您可以强制无论运算符优先级首先，计算该表达式。 若要强制上面的示例以首先执行加法运算，则无法将它重写如以下示例所示。  
  
 `x = z * (y + 4)`  
  
 前面的示例将添加`y`并`4`，然后将相乘的总值`z`。  
  
### <a name="nested-parenthetical-expressions"></a>嵌套的括号表达式  
 可以嵌套的括号来进一步重写优先级的多个级别中的表达式。 嵌套最深，依次类推到至少深度嵌套的而最后表达式括号外的下一个后跟首先，计算这些表达式最深嵌套在括号中。 下面的示例阐释了这一点。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 在前面的示例中，`z + 2`是首先计算，则其他带括号的表达式。 求幂，正常的优先级高于加法或乘法，是在此示例中最后评估，因为其他表达式括在括号中。  
  
## <a name="see-also"></a>请参阅

- [在 Visual Basic 中的算术运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [在 Visual Basic 中的比较运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [逻辑/按位运算符 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [布尔表达式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [值的比较](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [如何：计算数值](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic 中的运算符优先级](../../../../visual-basic/language-reference/operators/operator-precedence.md)
