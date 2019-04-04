---
title: While...End While 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843703"
---
# <a name="whileend-while-statement-visual-basic"></a>While...End While 语句 (Visual Basic)
只要给定的条件是运行一系列语句`True`。  
  
## <a name="syntax"></a>语法  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`condition`|必需。 `Boolean` 表达式。 如果`condition`是`Nothing`，Visual Basic 会将其视为`False`。|  
|`statements`|可选。 一个或多个语句之后`While`，其中每次运行`condition`是`True`。|  
|`Continue While`|可选。 将控制转移到的下一个迭代`While`块。|  
|`Exit While`|可选。 将控制的转移`While`块。|  
|`End While`|必需。 终止 `While` 块的定义。|  
  
## <a name="remarks"></a>备注  
 使用`While...End While`结构，当你想要重复执行一系列语句无限的次数，前提是在条件保持`True`。 如果想要更灵活地使用测试条件以及针对什么结果进行测试，您可能倾向于[执行操作...循环语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。 如果你想要重复执行语句，一定的时间，[为...下一条语句](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是更好的选择。  
  
> [!NOTE]
>  `While`关键字还用于[执行操作...循环语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)，则[Skip While 子句](../../../visual-basic/language-reference/queries/skip-while-clause.md)并且[Take While 子句](../../../visual-basic/language-reference/queries/take-while-clause.md)。  
  
 如果`condition`是`True`，则所有的`statements`运行，直至`End While`遇到语句。 随后控制返回到`While`语句，和`condition`再次检查。 如果`condition`仍是`True`，重复该过程。 如果它具有`False`，控制将传递到后面的语句`End While`语句。  
  
 `While`语句始终检查条件，然后会启动循环。 循环的条件的同时继续`True`。 如果`condition`是`False`时您首次进入循环，它不能甚至一次运行。  
  
 `condition`通常的比较结果的两个值，但它可以是任何表达式的计算结果为[布尔数据类型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。 此表达式可包含其他数据类型，例如数值类型，已转换为的值`Boolean`。  
  
 可以嵌套`While`上来将另一个循环内的循环。 此外可以嵌套在另一个控制结构的不同种类。 有关详细信息，请参阅[嵌套控制结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-while"></a>退出时  
 [退出时](../../../visual-basic/language-reference/statements/exit-statement.md)语句可以提供另一种方法退出`While`循环。 `Exit While` 立即将控制权移交给后面的语句`End While`语句。  
  
 通常使用`Exit While`对某些条件的求值后 (例如，在`If...Then...Else`结构)。 您可能需要退出循环，如果检测到导致其不必要或无法继续循环访问，例如错误的值或终止请求的条件。 可以使用`Exit While`在您测试条件可能会导致*无限循环*，这是可以运行次数极大甚至无限循环。 然后，可以使用`Exit While`来退出循环。  
  
 可以将任意数量的放置`Exit While`中的任意位置语句`While`循环。  
  
 当使用内嵌套`While`循环，`Exit While`控制权从最里面的循环和到下一个较高级别的嵌套。  
  
 `Continue While`语句立即将控制转移到循环的下一个迭代。 有关详细信息，请参阅[Continue 语句](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
## <a name="example"></a>示例  
 在以下示例中，在循环中的语句继续运行，直到`index`变量是否大于 10。  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`Continue While`和`Exit While`语句。  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a>示例  
 下面的示例读取在文本文件中的所有行。 <xref:System.IO.File.OpenText%2A>方法打开文件并返回<xref:System.IO.StreamReader>读取字符。 在中`While`条件，请<xref:System.IO.StreamReader.Peek%2A>方法的`StreamReader`确定文件是否包含其他字符。  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a>请参阅

- [循环结构](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Do...Loop 语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean 数据类型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [嵌套的控件结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 语句](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Continue 语句](../../../visual-basic/language-reference/statements/continue-statement.md)
