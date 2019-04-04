---
title: Do...Loop 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 3ff3d67f38f510b798da3e470de066cff1e98f29
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826036"
---
# <a name="doloop-statement-visual-basic"></a>Do...Loop 语句 (Visual Basic)
重复块语句时`Boolean`是条件`True`或直到条件变为`True`。  
  
## <a name="syntax"></a>语法  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`Do`|必需。 启动的定义`Do`循环。|  
|`While`|必选项（除非使用了 `Until`）。 重复循环，直到`condition`是`False`。|  
|`Until`|必选项（除非使用了 `While`）。 重复循环，直到`condition`是`True`。|  
|`condition`|可选。 `Boolean` 表达式。 如果`condition`是`Nothing`，Visual Basic 会将其视为`False`。|  
|`statements`|可选。 一个或多个语句时，或直到，重复`condition`是`True`。|  
|`Continue Do`|可选。 将控制转移到的下一个迭代`Do`循环。|  
|`Exit Do`|可选。 将控制的转移`Do`循环。|  
|`Loop`|必需。 终止的定义`Do`循环。|  
  
## <a name="remarks"></a>备注  
 使用`Do...Loop`结构，当你想要重复执行一系列语句无限的次数，直到满足某个条件。 如果你想要重复执行语句，一定的时间，[为...下一条语句](../../../visual-basic/language-reference/statements/for-next-statement.md)通常是更好的选择。  
  
 你可以使用`While`或`Until`来指定`condition`，但不可同时使用两者。  
  
 你可以测试`condition`仅一次的开头或循环的末尾。 如果测试`condition`循环的开头 (在`Do`语句)，该循环可能无法运行它甚至一次。 如果测试在循环末尾 (在`Loop`语句)，循环始终运行至少一次。  
  
 条件通常从两个值的比较结果，但它可以是任何表达式的计算结果为[布尔数据类型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)值 (`True`或`False`)。 这包括其他数据类型，例如，已转换为数值类型的值`Boolean`。  
  
 可以嵌套`Do`放置另一个循环内的循环。 此外可以嵌套不同类型的控制结构彼此内。 有关详细信息，请参阅[嵌套控制结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
> [!NOTE]
>  `Do...Loop`结构为您提供了更大的灵活性比[时...结束 While 语句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)因为它使您可以决定是否要结束循环时`condition`停止正在`True`或第一次为`True`。 它还使您可以测试`condition`的开头或循环的末尾。  
  
## <a name="exit-do"></a>退出 Do  
 [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md)语句可以提供了一种退出`Do…Loop`。 `Exit Do` 立即将控制转移到后面的语句`Loop`语句。  
  
 `Exit Do` 通常用于计算某些条件，例如，在之后`If...Then...Else`结构。 您可能需要退出循环，如果检测到导致其不必要或无法继续循环访问，例如错误的值或终止请求的条件。 一种用途`Exit Do`是要测试一个条件，可能会导致*无限循环*，这是一个循环，无法运行大型或甚至无限数量的次数。 可以使用`Exit Do`来退出循环。  
  
 可以包含任意数量的`Exit Do`中的任意位置语句`Do…Loop`。  
  
 当使用内嵌套`Do`循环，`Exit Do`控制权从最里面的循环和到下一个较高级别的嵌套。  
  
## <a name="example"></a>示例  
 在以下示例中，在循环中的语句继续运行，直到`index`变量是否大于 10。 `Until`子句在循环的末尾处。  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a>示例  
 下面的示例使用`While`子句而不是`Until`子句，和`condition`的循环，而不是结束时开始时测试。  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a>示例  
 在以下示例中，`condition`停止该循环时`index`变量是否大于 100。 `If`语句在循环中，但是，导致`Exit Do`语句停止循环索引变量是否大于 10 时。  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a>示例  
 下面的示例读取在文本文件中的所有行。 <xref:System.IO.File.OpenText%2A>方法打开文件并返回<xref:System.IO.StreamReader>读取字符。 在中`Do...Loop`条件，请<xref:System.IO.StreamReader.Peek%2A>方法的`StreamReader`确定是否存在任何其他字符。  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a>请参阅

- [循环结构](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [For...Next 语句](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Boolean 数据类型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [嵌套的控件结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 语句](../../../visual-basic/language-reference/statements/exit-statement.md)
- [While...End While 语句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
