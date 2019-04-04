---
title: Visual Basic 中的逻辑运算符和位运算符
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: ac47b6d7fa4861d18646a23f442caccc4062852f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819302"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic 中的逻辑运算符和位运算符
逻辑运算符比较`Boolean`表达式，并返回`Boolean`结果。 `And`， `Or`， `AndAlso`， `OrElse`，并`Xor`运算符是*二进制*因为它们采用两个操作数，而`Not`运算符是*一元*因为它采用单个操作数。 这些运算符的一些可以执行对整数值的按位逻辑运算。  
  
## <a name="unary-logical-operator"></a>一元逻辑运算符  
 [Not 运算符](../../../../visual-basic/language-reference/operators/not-operator.md)执行逻辑*求反运算*上`Boolean`表达式。 它将产生其操作数的逻辑反。 如果表达式的计算结果`True`，然后`Not`返回`False`; 如果表达式的计算结果`False`，然后`Not`返回`True`。 下面的示例阐释了这一点。  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>二元逻辑运算符  
 [And 运算符](../../../../visual-basic/language-reference/operators/and-operator.md)执行逻辑*一起*对两个`Boolean`表达式。 如果这两个表达式的计算结果为`True`，然后`And`返回`True`。 如果至少一个表达式的计算结果为`False`，然后`And`返回`False`。  
  
 [或运算符](../../../../visual-basic/language-reference/operators/or-operator.md)执行逻辑*析取*或*包含*对两个`Boolean`表达式。 如果任一表达式计算结果为`True`，或两者的计算结果`True`，然后`Or`返回`True`。 如果任一表达式计算结果为`True`，`Or`返回`False`。  
  
 [Xor 运算符](../../../../visual-basic/language-reference/operators/xor-operator.md)执行逻辑*排除*对两个`Boolean`表达式。 如果一个表达式的计算结果为`True`，但不是能同时`Xor`返回`True`。 如果这两个表达式的计算结果为`True`或两者的计算结果`False`，`Xor`返回`False`。  
  
 下面的示例阐释`And`， `Or`，和`Xor`运算符。  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>短路逻辑操作  
 [AndAlso 运算符](../../../../visual-basic/language-reference/operators/andalso-operator.md)非常类似于`And`运算符，在于它还对两个执行逻辑与运算`Boolean`表达式。 这两个主要区别在于`AndAlso`表现出*短路*行为。 如果中的第一个表达式`AndAlso`表达式的计算结果`False`，然后第二个表达式未计算值，因为它不会改变最终结果，并`AndAlso`返回`False`。  
  
 同样， [OrElse 运算符](../../../../visual-basic/language-reference/operators/orelse-operator.md)执行短路逻辑或运算，对两个`Boolean`表达式。 如果中的第一个表达式`OrElse`表达式的计算结果`True`，然后第二个表达式未计算值，因为它不会改变最终结果，并`OrElse`返回`True`。  
  
### <a name="short-circuiting-trade-offs"></a>短路的权衡  
 短路可以通过不计算一个表达式，不能更改逻辑操作的结果来提高性能。 但是，如果该表达式执行其他操作，则短路将跳过这些操作。 例如，如果表达式包含调用`Function`过程中，如果该表达式，和中包含的任何其他代码不调用过程`Function`不会运行。 因此，该函数可能只是偶尔运行，并可能未正确测试。 程序逻辑可能依赖于中的代码或`Function`。  
  
 下面的示例说明了之间的差异`And`， `Or`，及其短路对应项。  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 在前面的示例，请注意，在一些重要代码`checkIfValid()`调用短路时不会运行。 第一个`If`语句也会调用`checkIfValid()`即使`12 > 45`返回`False`，这是因为`And`不会短路。 第二个`If`语句不会调用`checkIfValid()`，这是因为当`12 > 45`返回`False`，`AndAlso`会短路第二个表达式。 第三个`If`语句也会调用`checkIfValid()`即使`12 < 45`返回`True`，这是因为`Or`不会短路。 第四个`If`语句不会调用`checkIfValid()`，这是因为当`12 < 45`返回`True`，`OrElse`会短路第二个表达式。  
  
## <a name="bitwise-operations"></a>按位运算  
 按位运算的计算结果在二进制 (基数为 2) 窗体中的两个整数值。 它们进行比较的相应位置处的位，然后分配基于比较的值。 下面的示例演示`And`运算符。  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 前面的示例中设置的值`x`为 1。 由于以下原因发生这种情况：  
  
-   值被视为二进制文件：  
  
     以二进制形式的 3 = 011  
  
     以二进制形式的 5 = 101  
  
-   `And`运算符将二进制表示形式，一次的一个二进制位置 （位） 进行比较。 如果给定位置处的两个位都为 1，1 位于该位置在结果中。 如果任一位为 0，0 位于该位置在结果中。 在前面的示例这样，如下所示：  
  
     011 (3 以二进制形式)  
  
     101 (5 以二进制形式)  
  
     001 （以二进制形式，结果）  
  
-   结果将被视为小数。 001 的值是 1 的二进制表示形式，因此`x`= 1。  
  
 按位`Or`操作类似，只是一个 1 分配给结果位，如果一个或两个比较位为 1。 `Xor` 如果恰好有一个比较位 （不能同时） 为 1，1 赋给结果位。 `Not` 采用单个操作数和反转所有位，包括符号位，并将该值分配到的结果。 这意味着，对于已签名的正数和负数`Not`始终返回一个负值，而对于负数，`Not`始终返回一个值为正或零值。  
  
 `AndAlso`和`OrElse`运算符不支持按位运算。  
  
> [!NOTE]
>  只能对整型，可以执行按位运算。 按位运算可以继续操作之前，必须是浮点值转换为整型类型。  
  
## <a name="see-also"></a>请参阅

- [逻辑/按位运算符 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [布尔表达式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [在 Visual Basic 中的算术运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [在 Visual Basic 中的比较运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [在 Visual Basic 中的串联运算符](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [运算符的有效组合](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
