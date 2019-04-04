---
title: 如何：计算数值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: 33184d9be275f5e777ffd79c6dd4e3182d865de7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825743"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>如何：计算数值 (Visual Basic)
您可以计算通过使用数值表达式的数字值。 一个*数值表达式*会包含文本、 常量和变量表示数字值的表达式并处理这些值的运算符。  
  
## <a name="calculating-numeric-values"></a>计算数值  
  
#### <a name="to-calculate-a-numeric-value"></a>若要计算的数字值  
  
-   将一个或多个数字文本、 常量和变量组合到一个数值表达式。 下面的示例显示了一些有效的数值表达式。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     前三行显示文本、 常量和变量。 每个单独窗体的有效数值表达式。 最后一行显示了具有两个文本的变量的组合。  
  
     请注意，数值表达式不会不完整的 Visual Basic 语句本身组成。 作为一个完整的语句的一部分，必须使用表达式。  
  
#### <a name="to-store-a-numeric-value"></a>若要存储的数字值  
  
-   赋值语句可用于将分配给一个变量，数值表达式所表示的值，如以下示例所示。  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     在前面的示例中，相等运算符右侧的表达式的值 (`=`) 分配给变量`j`上左侧和右侧的运算符，因此`j`的计算结果为 276。  
  
     有关详细信息，请参阅[语句](../../../../visual-basic/language-reference/statements/index.md)。  
  
## <a name="multiple-operators"></a>多个运算符  
 如果数值表达式包含多个运算符，计算它们的顺序由运算符优先级的规则确定。 若要替代的运算符优先顺序规则，则将表达式括在括号内，如上面的示例; 中所示首先计算括住的表达式。  
  
#### <a name="to-override-normal-operator-precedence"></a>若要重写常规运算符优先级  
  
-   使用括号括住您想要首先执行的操作。 下面的示例显示了具有相同的操作数和运算符的两个不同的结果。  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     在前面的示例的计算`j`执行加法运算符 (`+`) 第一个因为两边的括号`(67 + i)`重写常规优先级和分配给的值`j`为 276 (4 次 69)。 计算`k`按正常优先级执行运算符 (`*`之前`+`)，并分配给的值`k`为 270 （268 加 2）。  
  
     有关详细信息，请参阅[在 Visual Basic 中的运算符优先级](../../../../visual-basic/language-reference/operators/operator-precedence.md)。  
  
## <a name="see-also"></a>请参阅

- [运算符和表达式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [值的比较](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [语句](../../../../visual-basic/language-reference/statements/index.md)
- [Visual Basic 中的运算符优先级](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [算术运算符](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [运算符的有效组合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
