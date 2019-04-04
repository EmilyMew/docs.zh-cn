---
title: For...Next 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 5d47d57b75005d5c13dbf8633981dfb2d57d3e90
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826322"
---
# <a name="fornext-statement-visual-basic"></a>For...Next 语句 (Visual Basic)
将一组语句重复指定的次数。  
  
## <a name="syntax"></a>语法  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>部件  
  
|部件|描述|  
|----------|-----------------|  
|`counter`|在所需`For`语句。 数值变量。 For 循环控制变量。 有关详细信息，请参阅[计数器参数](#BKMK_Counter)本主题中更高版本。|  
|`datatype`|可选。 数据类型的`counter`。 有关详细信息，请参阅[计数器参数](#BKMK_Counter)本主题中更高版本。|  
|`start`|必需。 数值表达式。 `counter` 的初始值。|  
|`end`|必需。 数值表达式。 最终值`counter`。|  
|`step`|可选。 数值表达式。 所根据的数量`counter`循环每次都会递增。|  
|`statements`|可选。 一个或多个语句之间`For`和`Next`运行指定的次数。|  
|`Continue For`|可选。 将控制转移到下一步的循环迭代。|  
|`Exit For`|可选。 将控制的转移`For`循环。|  
|`Next`|必需。 终止的定义`For`循环。|  
  
> [!NOTE]
>  `To`关键字用于在此语句中指定计数器的范围。 您还可以使用此关键字在[选择...Case 语句](../../../visual-basic/language-reference/statements/select-case-statement.md)和数组声明中。 有关数组声明的详细信息，请参阅[Dim 语句](../../../visual-basic/language-reference/statements/dim-statement.md)。  
  
## <a name="simple-examples"></a>简单的示例  
 您使用`For`...`Next`结构，当你想要重复次数的一组语句。  
  
 在以下示例中，`index`变量开头的值为 1，并会在循环结束后的值的每次迭代时递增`index`达到 5。  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 在以下示例中，`number`变量从 2 开始，将降低在循环结束后的值的每次迭代 0.25`number`达到 0。 `Step`自变量的`-.25`降低 0.25 循环的每个迭代上的值。  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
>  一个[时...While 语句结束](../../../visual-basic/language-reference/statements/while-end-while-statement.md)或[执行操作...循环语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)正常时你事先不知道在多少次循环中运行这些语句。 但是，如果您希望运行特定次数的循环`For`...`Next`循环是更好的选择。 当您首次进入循环时确定迭代的次数。  
  
## <a name="nesting-loops"></a>嵌套循环  
 可以嵌套`For`放置另一个循环内的循环。 下面的示例演示嵌套`For`...`Next`具有不同的步骤值的结构。 外部循环创建循环每次迭代的字符串。 内部循环减小该循环每次迭代的循环计数器变量。  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 当嵌套循环，每个循环必须具有一个唯一`counter`变量。  
  
 此外可以嵌套不同类型中每个其他控制结构。 有关详细信息，请参阅[嵌套控制结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)。  
  
## <a name="exit-for-and-continue-for"></a>有关退出并继续  
 `Exit For`语句立即退出`For`...`Next` 到后面的语句的循环，并将控制权`Next`语句。  
  
 `Continue For`语句控制将立即转移到循环的下一个迭代。 有关详细信息，请参阅[Continue 语句](../../../visual-basic/language-reference/statements/continue-statement.md)。  
  
 下面的示例演示如何使用`Continue For`和`Exit For`语句。  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 可以将任意数量的`Exit For`中的语句`For`...`Next` 循环。 当使用内嵌套`For`...`Next` 循环、`Exit For`退出最里面的循环，并将控制转移到下一个较高级别的嵌套。  
  
 `Exit For` 通常使用后评估某些条件 (例如，在`If`...`Then`...`Else`结构)。 您可能想要使用`Exit For`满足以下条件：  
  
-   继续循环访问是不必要或不可能。 错误的值或终止请求可能会创建这种情况。  
  
-   一个`Try`...`Catch`...`Finally`语句捕获异常。 可以使用`Exit For`末尾的`Finally`块。  
  
-   具有无限循环，这是一个循环，无法运行大型或甚至无限数量的次数。 如果检测到此类情况，可以使用`Exit For`来退出循环。 有关详细信息，请参阅[执行操作...循环语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)。  
  
## <a name="technical-implementation"></a>技术实现  
 当`For`...`Next`循环开始，Visual Basic 的计算结果`start`， `end`，和`step`。 Visual Basic 仅在此时间，然后将计算这些值`start`到`counter`。 在之前的语句块将运行，Visual Basic 进行比较`counter`到`end`。 如果`counter`已经是大于`end`值 (或较小的 if`step`为负)，则`For`循环结束并将控制权传递到后面的语句`Next`语句。 否则，在运行语句块。  
  
 每次 Visual Basic 遇到`Next`语句，则会递增`counter`通过`step`，并返回到`For`语句。 再次进行比较`counter`到`end`，并再次运行块或者退出循环，具体取决于结果。 此过程将继续，直至`counter`传递`end`或`Exit For`遇到语句。  
  
 循环不会阻止直到`counter`已通过`end`。 如果`counter`等同于`end`，循环继续。 确定是否运行的块的比较`counter`  <=  `end`如果`step`为正并`counter`  >=  `end`如果`step`为负。  
  
 如果您更改的值`counter`内部循环中，你的代码可能更难以阅读和调试。 更改的值`start`， `end`，或`step`不会影响已确定时首次进入循环的迭代值。  
  
 如果嵌套循环，编译器将发出错误信号它是否会遇到`Next`外部的嵌套级别之前, 的语句`Next`内部级别的语句。 但是，编译器可检测到这只有在指定重叠错误`counter`中每个`Next`语句。  
  
### <a name="step-argument"></a>步骤参数  
 值`step`可以为正数或负数。 此参数确定循环处理根据下表：  
  
|**步长值**|**如果，执行循环**|  
|--------------------|--------------------------|  
|正或零|`counter` <= `end`|  
|负数|`counter` >= `end`|  
  
 默认值`step`为 1。  
  
### <a name="BKMK_Counter"></a> 计数器参数  
 下表指示是否`counter`定义新的本地变量为作用域为整个`For…Next`循环。 此决定取决于是否`datatype`存在以及是否`counter`已定义。  
  
|是`datatype`存在？|是`counter`已定义？|结果 (是否`counter`定义新的本地变量为作用域为整个`For...Next`循环)|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|否|是|不可以，因为`counter`已定义。 如果范围`counter`不是本地的过程中，将出现编译时警告。|  
|否|否|可以。 从推断的数据类型`start`， `end`，和`step`表达式。 有关类型推理的信息，请参阅[Option Infer 语句](../../../visual-basic/language-reference/statements/option-infer-statement.md)并[本地类型推断](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)。|  
|是|是|是的但是只有当现有`counter`外部过程定义的变量。 该变量保持独立。 如果现有范围`counter`变量是本地的过程中，将发生编译时错误。|  
|是|否|可以。|  
  
 数据类型的`counter`确定的类型的迭代，它必须是以下类型之一：  
  
-   一个`Byte`， `SByte`， `UShort`， `Short`， `UInteger`， `Integer`， `ULong`， `Long`， `Decimal`， `Single`，或`Double`。  
  
-   使用声明的枚举[Enum 语句](../../../visual-basic/language-reference/statements/enum-statement.md)。  
  
-   一个 `Object`。  
  
-   一种类型`T`具有以下运算符，其中`B`是一种可在`Boolean`表达式。  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 您可以选择指定`counter`变量中`Next`语句。 此语法可提高应用程序的可读性，尤其是在具有嵌套`For`循环。 必须指定的变量，将显示在相应`For`语句。  
  
 `start`， `end`，并`step`表达式可以计算为任何数据类型为的类型扩展`counter`。 如果使用的用户定义类型`counter`，可能需要定义`CType`转换运算符，以将类型的转换`start`， `end`，或`step`为的类型`counter`。  
  
## <a name="example"></a>示例  
 下面的示例从一个泛型列表中移除所有元素。 而不是[为每个...下一条语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)，该示例演示了`For`...`Next`按降序顺序循环访问的语句。 该示例使用此方法，因为`removeAt`方法将导致触发 after 已移除的元素具有较低的索引值的元素。  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>示例  
 下面的示例循环访问使用声明的枚举[Enum 语句](../../../visual-basic/language-reference/statements/enum-statement.md)。  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>示例  
 在以下示例中，语句参数使用具有运算符重载的类`+`， `-`， `>=`，和`<=`运算符。  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Collections.Generic.List%601>
- [循环结构](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While 语句](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop 语句](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [嵌套的控件结构](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit 语句](../../../visual-basic/language-reference/statements/exit-statement.md)
- [集合](../../programming-guide/concepts/collections.md)
