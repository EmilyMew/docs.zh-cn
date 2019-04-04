---
title: 比较运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 9014cac5e2f3933b27411dfe5681fc16f4cdde30
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821031"
---
# <a name="comparison-operators-visual-basic"></a>比较运算符 (Visual Basic)
以下是定义在 Visual Basic 中的比较运算符。  
  
 `<` 运算符  
  
 `<=` 运算符  
  
 `>` 运算符  
  
 `>=` 运算符  
  
 `=` 运算符  
  
 `<>` 运算符  
  
 [Is 运算符](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot 运算符](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like 运算符](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 这些运算符比较两个表达式以确定它们相等，以及如果不是，它们之间的区别。 `Is``IsNot`，和`Like`详细讨论了在单独的帮助页上。 关系比较运算符在此页上详细讨论。  
  
## <a name="syntax"></a>语法  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>部件  
 `result`  
 必需。 一个`Boolean`值，该值表示比较结果。  
  
 `expression`  
 必需。 任何表达式。  
  
 `comparisonoperator`  
 必需。 任何关系比较运算符。  
  
 `object1`， `object2`  
 必需。 任何引用对象名称。  
  
 `string`  
 必需。 任何 `String` 表达式。  
  
 `pattern`  
 必需。 任何`String`表达式或一系列字符。  
  
## <a name="remarks"></a>备注  
 下表包含一系列关系比较运算符和条件，来确定是否`result`是`True`或`False`。  
  
|运算符|`True` 是否|`False` 是否|  
|--------------|---------------|----------------|  
|`<` （小于）|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=` （小于或等于）|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>` （大于）|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=` （大于或等于）|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=` （等于）|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>` （不等于）|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [= 运算符](../../../visual-basic/language-reference/operators/assignment-operator.md)还用作赋值运算符。  
  
 `Is`运算符`IsNot`运算符，和`Like`运算符具有特定的比较功能，不同于上表中的运算符。  
  
## <a name="comparing-numbers"></a>将数字进行比较  
 当比较类型的表达式`Single`类型之一`Double`，则`Single`表达式转换为`Double`。 此行为是与 Visual Basic 6 中所发现的行为相反。  
  
 同样，当比较类型的表达式`Decimal`类型的表达式`Single`或`Double`，则`Decimal`表达式转换为`Single`或`Double`。 有关`Decimal`表达式中，任何小数部分的值小于 1E 28 可能会丢失。 此类的小数部分值丢失可能导致两个值时它们不是比较结果为相等。 出于此原因，请注意，当使用等式 (`=`) 比较两个浮点变量。 它是差异的更安全，若要测试是否两个数字之间的绝对值是差异的小于较小的可接受容差。  
  
### <a name="floating-point-imprecision"></a>浮点不精确性  
 当使用浮点数时，请注意在内存中不一定有精确的表示形式。 这可能导致意外的结果从某些操作，如值比较， [Mod 运算符](../../../visual-basic/language-reference/operators/mod-operator.md)。 有关详细信息，请参阅[故障排除数据类型](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## <a name="comparing-strings"></a>比较字符串  
 当比较字符串时，基于它们按字母顺序排序的顺序，具体取决于计算这些字符串表达式`Option Compare`设置。  
  
 `Option Compare Binary` 基本的字符串比较派生自的内部二进制表示形式的字符的排序顺序。 排序顺序取决于代码页。 下面的示例显示了典型的二进制排序顺序。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` 基本的字符串由应用程序的区域设置的不区分大小写的文本排序顺序的比较。 当您将设置`Option Compare Text`和对在前面的示例字符进行排序，以下文本排序顺序应用：  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>区域设置相关性  
 当您将设置`Option Compare Text`，字符串比较的结果可能取决于应用程序运行所在的区域设置。 两个字符可能会比较结果相等，但不是在另一个区域设置中。 如果使用的字符串比较来做出重要决策，例如是否接受尝试登录，你应该于区域设置敏感度的警报。 这两个设置，请考虑`Option Compare Binary`或调用<xref:Microsoft.VisualBasic.Strings.StrComp%2A>，这会考虑区域设置。  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>关系比较运算符使用无类型编程  
 使用具有关系比较运算符`Object`下不允许使用表达式`Option Strict On`。 当`Option Strict`是`Off`，并将`expression1`或`expression2`是`Object`表达式中，运行时类型确定如何比较。 下表显示了如何比较表达式和比较，具体取决于操作数的运行时类型的结果。  
  
|如果操作数均为|比较|  
|---------------------|-------------------|  
|两者 `String`|排序基于字符串排序特征进行比较。|  
|这两个数字|对象转换为`Double`，数值比较。|  
|一个数值，另一个 `String`|`String`转换为`Double`并执行数值比较。 如果`String`不能转换为`Double`、<xref:System.InvalidCastException>引发。|  
|或者两种方法是以外的其他引用类型 `String`|引发 <xref:System.InvalidCastException>。|  
  
 数值比较将`Nothing`为 0。 字符串比较将视为`Nothing`作为`""`（空字符串）。  
  
## <a name="overloading"></a>重载  
 关系比较运算符 (`<`。 `<=``>`， `>=`， `=`， `<>`) 可以是*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 如果你的代码使用任何这些运算符对这样的类或结构，请确保了解重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
 请注意， [= 运算符](../../../visual-basic/language-reference/operators/assignment-operator.md)仅作为关系比较运算符，而不是赋值运算符可以进行重载。  
  
## <a name="example"></a>示例  
 下面的示例显示了关系比较运算符，用来比较表达式的各种用法。 关系比较运算符将返回`Boolean`表示是否规定的表达式计算结果为结果`True`。 当应用`>`和`<`运算符对字符串进行比较使用正常的字符串按字母顺序排序顺序。 此顺序可以是依赖于区域设置。 排序是否是区分大小写取决于[Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)设置。  
  
 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]  
  
 在上述示例中，第一次比较将返回`False`和其余的比较返回`True`。  
  
## <a name="see-also"></a>请参阅

- <xref:System.InvalidCastException>
- [= 运算符](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [数据类型疑难解答](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [在 Visual Basic 中的比较运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
