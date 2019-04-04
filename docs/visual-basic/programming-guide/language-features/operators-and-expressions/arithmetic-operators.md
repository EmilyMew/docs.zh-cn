---
title: 算术运算符 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: 635c791f81107a1800e2ef381f6bea78cbc18e18
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820764"
---
# <a name="arithmetic-operators-in-visual-basic"></a>算术运算符 (Visual Basic)
算术运算符用于执行许多熟悉涉及计算的数字表示的文本、 变量、 其他表达式、 函数和属性调用和常量的值的算术运算。 此外属于算术运算符将移位运算符，它在操作数的单个位级别上执行操作并向左或向右移动其位模式。  
  
## <a name="arithmetic-operations"></a>算术运算  
 可以一起使用的表达式中添加两个值[+ 运算符](../../../../visual-basic/language-reference/operators/addition-operator.md)，或从另一个具有中减去 1 [-运算符 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，如下面的示例所示。  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 此外使用求反[-运算符 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)，但只有一个操作数，如以下示例所示。  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 使用乘法和除法[* 运算符](../../../../visual-basic/language-reference/operators/multiplication-operator.md)并[/ 运算符 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)分别，如以下示例所示。  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 使用求幂[^ 运算符](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)，如下面的示例所示。  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 整数除法利用执行[\ 运算符 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)。 整数除法返回商，即表示的次数的整数除数可以将划分成而无需考虑任何其余部分被除数。 除数和被除数必须是整型类型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，和`ULong`) 为此运算符。 必须首先将所有其他类型转换为整型类型。 下面的示例演示了整数除法。  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 使用执行取模算术[Mod 运算符](../../../../visual-basic/language-reference/operators/mod-operator.md)。 此运算符返回其余部分被除数除以除数后一个整数的次数。 如果除数和被除数的整数类型，返回的值是整数。 如果除数和除数是浮点类型，返回的值也是浮点。 下面的示例演示此行为。  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>尝试的除数为零  
 被零除具有不同的结果，具体取决于所涉及的数据类型。 整型部门中 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`)，则[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]引发<xref:System.DivideByZeroException>异常。 在除法运算`Decimal`或`Single`数据类型[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]还会引发<xref:System.DivideByZeroException>异常。  
  
 浮点划分方式涉及`Double`数据类型，不会引发异常，并且结果是表示的类成员<xref:System.Double.NaN>， <xref:System.Double.PositiveInfinity>，或<xref:System.Double.NegativeInfinity>，取决于被除数。 下表汇总了各个结果的尝试除`Double`为零的值。  
  
|被除数的数据类型|除数数据类型|被除数的值|结果|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> （不是数学上定义的数字）|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 当捕获<xref:System.DivideByZeroException>异常，您可以使用其成员来帮助你对其进行处理。 例如，<xref:System.Exception.Message%2A>属性包含异常的消息文本。 有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。  
  
## <a name="bit-shift-operations"></a>移位运算  
 移位操作对位模式执行算术移位运算。 而在右侧的操作数中指定数目的位置，若要切换模式，模式都包含在左侧的操作数。 将模式切换到右[>> 运算符](../../../../visual-basic/language-reference/operators/right-shift-operator.md)或使用左侧[<< 运算符](../../../../visual-basic/language-reference/operators/left-shift-operator.md)。  
  
 模式操作数的数据类型必须是`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`，或`ULong`。 移位量操作数的数据类型必须是`Integer`或必须扩大到`Integer`。  
  
 算术移位不是循环，这意味着移出结果的一端的数位另一端不重新移入。 因 shift 而空出的位设置，如下所示：  
  
-   0 表示算术左移位运算  
  
-   算术右移位运算的一个正数，数字为 0  
  
-   算术右移位运算的无符号的数据类型为 0 (`Byte`， `UShort`， `UInteger`， `ULong`)  
  
-   1 表示算术右移位运算的负号 (`SByte`， `Short`， `Integer`，或`Long`)  
  
 下面的示例将转移`Integer`左侧和右侧值。  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 算术移位永远不会产生溢出异常。  
  
## <a name="bitwise-operations"></a>按位运算  
 逻辑运算符，除了`Not`， `Or`， `And`，和`Xor`还执行按位算术运算时使用对数字值。 详细信息，请参阅"按位操作"中[逻辑和位运算符在 Visual Basic 中](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)。  
  
## <a name="type-safety"></a>类型安全  
 操作数通常应为同一类型。 例如，如果你正在使用的加法`Integer`变量，您应将其添加到另一个`Integer`变量，并且您应将结果分配给类型的变量的`Integer`也。  
  
 一种方法以确保良好的类型安全编码做法是使用[Option Strict 语句](../../../../visual-basic/language-reference/statements/option-strict-statement.md)。 如果您设置`Option Strict On`，Visual Basic 会自动执行*类型安全*转换。 例如，如果你尝试添加`Integer`变量`Double`变量并向其分配值`Double`变量，该操作将正常进行，因为`Integer`值可以转换为`Double`而不丢失数据。 类型不安全的转换，但是，导致编译器错误与`Option Strict On`。 例如，如果你尝试添加`Integer`变量`Double`变量并向其分配值`Integer`变量时，会导致编译器错误，因为`Double`变量不能隐式转换为键入`Integer`。  
  
 如果您设置`Option Strict Off`，但是，Visual Basic 允许隐式收缩转换才能开始，但是它们可能会导致意外丢失数据或精度。 出于此原因，我们建议你使用`Option Strict On`编写生产代码时。 有关详细信息，请参阅 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)。  
  
## <a name="see-also"></a>请参阅

- [算术运算符](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [移位运算符](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [在 Visual Basic 中的比较运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [在 Visual Basic 中的串联运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [在 Visual Basic 中的逻辑和位运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [运算符的有效组合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
