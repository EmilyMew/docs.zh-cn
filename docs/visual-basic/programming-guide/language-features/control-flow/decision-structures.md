---
title: 决策结构 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 20b60fb425278dacb56ee5f888967554a1f76aeb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825373"
---
# <a name="decision-structures-visual-basic"></a>决策结构 (Visual Basic)
Visual Basic，可以测试条件，然后执行不同操作，具体取决于该测试的结果。 你可以测试条件是 true 或 false 的各种值的表达式，或生成时执行的一系列语句的各种异常。  
  
 下图显示了测试条件为 true，并采用不同的操作，具体取决于是否，则返回 true 或 false 的决策结构。  
  
 ![If 的流程图...然后...其他构造](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
条件为 true，并且为 false 时执行不同操作  
  
## <a name="ifthenelse-construction"></a>如果...然后...其他构造  
 `If...Then...Else` 构造，可以对一个或多个条件测试，并运行一个或多个语句，具体取决于每个条件。 您可以测试条件，然后按以下方式执行操作：  
  
-   如果条件为，运行一个或多个语句 `True`  
  
-   如果条件为，运行一个或多个语句 `False`  
  
-   如果条件为运行某些语句`True`和其他人是否它 `False`  
  
-   如果前一个条件为，测试其他条件 `False`  
  
 提供了所有这些可能性的控制结构是[如果...然后...Else 语句](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)。 如果你有一个测试和运行一个语句，可以使用单个行版本。 如果有一组更复杂的条件和操作，您可以使用多个行版本。  
  
## <a name="selectcase-construction"></a>选择...Case 构造  
 `Select...Case`构造可以评估一次表达式并运行不同的语句基于不同的可能值集。 有关详细信息，请参阅[选择...Case 语句](../../../../visual-basic/language-reference/statements/select-case-statement.md)。  
  
## <a name="trycatchfinally-construction"></a>重试...Catch...最后构造  
 `Try...Catch...Finally` 构造，可以运行一组保留控件，如果您的语句的任何一个导致异常的环境下的语句。 您可以采取不同操作的不同异常。 您可以选择指定的退出整个之前运行的代码块`Try...Catch...Finally`构造，而不考虑所发生的情况。 有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
> [!NOTE]
>  许多控件结构，当您单击某个关键字在结构中的关键字的所有突出显示。 例如，单击`If`中`If...Then...Else`构造、 的所有实例`If`， `Then`， `ElseIf`， `Else`，和`End If`构造中将突出显示。 若要将移动到下一步或上一个突出显示关键字，按 CTRL + SHIFT + 向下键或 CTRL + SHIFT + 向上键。  
  
## <a name="see-also"></a>请参阅

- [控制流](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [循环结构](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [其他控件结构](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [嵌套的控件结构](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If 运算符](../../../../visual-basic/language-reference/operators/if-operator.md)
