---
title: If 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 9ab01755d75c91ce87acf83e7f406b26c466aef6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834629"
---
# <a name="if-operator-visual-basic"></a>If 运算符 (Visual Basic)
使用短路计算有条件地返回两个值之一。 `If`带有三个参数或两个参数，可以调用运算符。  
  
## <a name="syntax"></a>语法  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>如果使用三个自变量调用运算符  
 当`If`调用通过使用三个参数，第一个参数必须为一个值，可以强制转换为`Boolean`。 `Boolean`值将确定哪些其他两个参数是进行计算并返回。 下面的列表仅适用于`If`使用三个自变量调用运算符。  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`argument1`|必需。 `Boolean`。 确定哪些要计算并返回的其他参数。|  
|`argument2`|必需。 `Object`。 计算并返回 if`argument1`计算结果为`True`。|  
|`argument3`|必需。 `Object`。 计算并返回 if`argument1`计算结果为`False`或者如果`argument1`是[Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`变量的计算结果为[Nothing](../../../visual-basic/language-reference/nothing.md)。|  
  
 `If`运算符，它使用三个自变量调用的工作方式类似于`IIf`函数，但它使用短路计算。 `IIf`函数始终计算所有三个参数，而`If`具有三个自变量的运算符都要都计算其中只有两个。 第一个`If`自变量计算并将结果转换为`Boolean`值，`True`或`False`。 如果值为`True`，`argument2`是进行计算并返回其值，但`argument3`则不会评估。 如果的值`Boolean`表达式是`False`，`argument3`是进行计算并返回其值，但`argument2`则不会评估。 下面的示例说明如何使用`If`使用了三个参数：  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 下面的示例说明了的价值短路计算。 该示例显示了两次尝试将变量`number`由变量`divisor`例外`divisor`为零。 在这种情况下，应返回 0，并且不应尝试执行该除法运算，否则会导致运行时错误。 因为`If`中使用表达式短路计算时，将计算第二个或第三个参数，具体取决于第一个参数的值。 如果第一个参数为 true，除数不为零，则可以安全地评估第二个参数，并执行该除法运算。 如果第一个参数为 false，计算仅第三个参数，并返回 0。 因此，如果除数为 0，任何尝试执行除法并不会产生错误。 但是，因为`IIf`不使用短路计算，即使第一个参数为 false，则计算第二个参数。 这将导致运行时被零除错误。  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>如果使用两个自变量调用运算符  
 第一个参数`If`可以省略。 这使操作员能够使用仅两个参数进行调用。 下面的列表仅适用于`If`使用两个自变量调用运算符。  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`argument2`|必需。 `Object`。 必须是引用或为 null 的类型。 进行计算并返回到的任何内容不是评估时`Nothing`。|  
|`argument3`|必需。 `Object`。 计算并返回 if`argument2`计算结果为`Nothing`。|  
  
 当`Boolean`省略参数，第一个参数必须是引用或为 null 的类型。 如果第一个参数的计算结果为`Nothing`，返回的第二个参数的值。 在所有其他情况下，返回第一个参数的值。 以下示例演示了如何进行此评估版。  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [可以为 null 的值类型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
