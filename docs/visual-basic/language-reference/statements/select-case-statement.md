---
title: Select...Case 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: f99db4f1dc224e5f75ee67ba94c3745f28438724
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814609"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case 语句 (Visual Basic)
在运行的语句，具体取决于表达式的值的多个组之一。  
  
## <a name="syntax"></a>语法  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>部件  
  
|术语|定义|  
|---|---|  
|`testexpression`|必需。 表达式。 计算结果必须为基本数据类型之一 (`Boolean`， `Byte`， `Char`， `Date`， `Double`， `Decimal`， `Integer`， `Long`， `Object`， `SByte`， `Short`，`Single`， `String`， `UInteger`， `ULong`，和`UShort`)。|  
|`expressionlist`|在所需`Case`语句。 表示匹配值的表达式子句的列表`testexpression`。 由逗号分隔多个表达式子句。 每个子句可以采用以下形式之一：<br /><br /> -   *expression1* `To` *expression2*<br />-   [ `Is` ] *comparisonoperator* *expression*<br />-   *expression*<br /><br /> 使用`To`关键字来指定匹配的范围边界值`testexpression`。 值`expression1`必须小于或等于的值`expression2`。<br /><br /> 使用`Is`关键字的比较运算符 (`=`， `<>`， `<`， `<=`， `>`，或者`>=`) 来指定匹配值的限制`testexpression`。 如果`Is`未提供关键字，它将自动插入之前*比较运算符*。<br /><br /> 仅指定窗体`expression`被视为一种特殊的情况`Is`形成 where*比较运算符*是等号 (`=`)。 此窗体评为`testexpression`  =  `expression`。<br /><br /> 中的表达式`expressionlist`可以为任何数据类型，则它们隐式转换为的类型`testexpression`适当`comparisonoperator`对与正在使用它的两种类型有效。|  
|`statements`|可选。 一个或多个语句之后`Case`，运行的如果`testexpression`匹配中的任何子句`expressionlist`。|  
|`elsestatements`|可选。 一个或多个语句之后`Case Else`，运行的如果`testexpression`不匹配中的任何子句`expressionlist`任何`Case`语句。|  
|`End Select`|终止的定义`Select`...`Case`构造。|  
  
## <a name="remarks"></a>备注  
 如果`testexpression`匹配任何`Case``expressionlist`子句中，之后的语句`Case`语句最多运行下一步`Case`， `Case Else`，或`End Select`语句。 控制权然后传递给后面的语句`End Select`。 如果`testexpression`匹配`expressionlist`中多个子句`Case`子句，仅第一个匹配之后的语句运行。  
  
 `Case Else`语句用于引入`elsestatements`之间不存在任何匹配时要运行`testexpression`和一个`expressionlist`中任何其他子句`Case`语句。 尽管没有要求，它是个好办法`Case Else`语句中的您`Select Case`构造来处理无法预料`testexpression`值。 如果没有`Case``expressionlist`子句匹配`testexpression`，并且没有任何`Case Else`语句，控制将传递到后面的语句`End Select`。  
  
 您可以使用多个表达式或范围中每个`Case`子句。 例如，下面的行是有效的。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is`中使用的关键字`Case`并`Case Else`语句不是与相同[Is 运算符](../../../visual-basic/language-reference/operators/is-operator.md)，用于对象的引用比较。  
  
 您可以指定范围和字符串使用多个表达式。 在以下示例中，`Case`匹配任何字符串，是完全相等"apples"、"螺母"和"soup"之间的值按字母顺序，或包含完全相同的值的当前值`testItem`。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 设置`Option Compare`可能会影响字符串比较。 下`Option Compare Text`，"苹果"和"apples"的字符串的比较结果相等，但在`Option Compare Binary`，它们不匹配。  
  
> [!NOTE]
>  一个`Case`包含多个子句的语句可能会表现出行为称为*短路*。 Visual Basic 从左到右，这些子句的计算结果和如果一个将生成与匹配`testexpression`，不计算剩余的子句。 短路可以提高性能，但它可以产生意外的结果，如果希望在每个表达式`expressionlist`要计算。 有关短路的详细信息，请参阅[布尔表达式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)。  
  
 如果中的代码`Case`或`Case Else`语句块不需要在块中运行任何其他语句，它可以使用退出块`Exit Select`语句。 此控件将立即转移到后面的语句`End Select`。  
  
 `Select Case` 构造可相互嵌套。 每个嵌套`Select Case`构造必须有一个匹配`End Select`语句，并且必须完全包含在单个`Case`或`Case Else`语句块的外部`Select Case`构造它嵌套在其中。  
  
## <a name="example"></a>示例  
 下面的示例使用`Select Case`构造来写入变量的值相对应的行`number`。 第二个`Case`语句包含的值相匹配的当前值`number`，因此该语句，它将写入"为 6 到 8，非独占"运行。  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End 语句](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else 语句](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare 语句](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit 语句](../../../visual-basic/language-reference/statements/exit-statement.md)
