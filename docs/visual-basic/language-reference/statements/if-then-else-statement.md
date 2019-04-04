---
title: If...Then...Else 语句 (Visual Basic)
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: d91a913d515f36a6b974850bc30079b000a919b4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842689"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else 语句 (Visual Basic)
根据表达式的值有条件地执行一组语句。  
  
## <a name="syntax"></a>语法  
  
```  
' Multiline syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  

## <a name="quick-links-to-example-code"></a>示例代码的快速链接

本文包括几个示例，展示了使用`If`...`Then`...`Else`语句：

* [多行语法示例](#multi-line)
* [嵌套的语法示例](#nested)
* [单行语法示例](#single-line)

## <a name="parts"></a>部件  
 `condition`  
 必需。 表达式。 计算结果必须为`True`或`False`，或为数据类型的隐式转换为`Boolean`。  
  
 如果表达式为[Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`变量的计算结果为[Nothing](../../../visual-basic/language-reference/nothing.md)，条件表达式时，都被视为`False`和`Else`执行块。  
  
 `Then`  
 需要在单个行的语法;在多行语法中可选。  
  
 `statements`  
 可选。 一个或多个语句之后`If`...`Then`如果执行的`condition`的计算结果为`True`。  
  
 `elseifcondition`  
 如果使用`ElseIf`存在。 表达式。 计算结果必须为`True`或`False`，或为数据类型的隐式转换为`Boolean`。  
  
 `elseifstatements`  
 可选。 一个或多个语句之后`ElseIf`...`Then`如果执行的`elseifcondition`的计算结果为`True`。  
  
 `elsestatements`  
 可选。 如果没有上一个执行的一个或多个语句`condition`或`elseifcondition`表达式计算结果为`True`。  
  
 `End If`  
 终止的多行版本`If`...`Then`...`Else`块。  
  
## <a name="remarks"></a>备注  
  
### <a name="multiline-syntax"></a>多行语法  
 当`If`...`Then`...`Else`遇到语句，`condition`进行测试。 如果`condition`是`True`之后的语句、`Then`执行。 如果`condition`是`False`，则每个`ElseIf`语句 （如果有的话） 按顺序计算。 当`True``elseifcondition`找到，则紧跟在关联的语句`ElseIf`执行。 如果没有`elseifcondition`计算结果为`True`，或者如果有任何`ElseIf`语句，之后的语句`Else`执行。 执行后面的语句后`Then`， `ElseIf`，或`Else`，继续后面的语句执行`End If`。  
  
 `ElseIf`和`Else`子句都是可选。 可以有任意多个`ElseIf`根据需要`If`...`Then`...`Else`语句，但不会`ElseIf`子句可以出现后`Else`子句。 `If`...`Then`...`Else`可以相互嵌套语句。  
  
 在多行的语法中，`If`语句必须是第一行的唯一语句。 `ElseIf`， `Else`，和`End If`可以仅按行标签前面语句。 `If`...`Then`...`Else`块必须结束`End If`语句。  
  
> [!TIP]
>  [选择...Case 语句](../../../visual-basic/language-reference/statements/select-case-statement.md)评估一个具有多个可能值的表达式时可能会更有用。  
  
### <a name="single-line-syntax"></a>单行语法  
 可以为一个条件，代码使用的单行语法执行如果为 true。 但是，多行语法提供了更多结构和大的灵活性和易于阅读、 维护和调试。  
  
 接下来`Then`关键字进行检查，以确定一个语句是否为单线条`If`。 如果注释之外的任何内容之后出现`Then`上的同一行中，该语句被视为单线条`If`语句。 如果`Then`不存在，它必须是多个行的开头`If`...`Then`...`Else`.  
  
 在单行语法中，可以有多个语句的结果作为执行`If`...`Then`决策。 所有语句必须位于同一行上，并以冒号分隔。  

## <a name="multiline-syntax-example"></a>多行语法示例

<a name="multi-line"></a>
 
 下面的示例演示如何使用多行的语法`If`...`Then`...`Else`语句。  
  
 [!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>嵌套的语法示例

<a name="nested"></a>

 下面的示例包含嵌套`If`...`Then`...`Else`语句。  
  
 [!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>单行语法示例
  
<a name="single-line"></a> 下面的示例演示如何使用单行语法。  
  
 [!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case 语句](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [嵌套的控件结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [决策结构](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If 运算符](../../../visual-basic/language-reference/operators/if-operator.md)
