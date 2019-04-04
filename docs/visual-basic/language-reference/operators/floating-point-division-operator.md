---
title: / 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: af2316f92e2904eee1e8c046b34b8147e40cb513
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825061"
---
# <a name="-operator-visual-basic"></a>/ 运算符 (Visual Basic)
使两个数字相除，返回浮点结果。  
  
## <a name="syntax"></a>语法  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>部件  
 `expression1`  
 必需。 任何数值表达式。  
  
 `expression2`  
 必需。 任何数值表达式。  
  
## <a name="supported-types"></a>支持的类型  
 所有数值类型，包括未签名和浮点类型和`Decimal`。  
  
## <a name="result"></a>结果  
 结果是完整的商`expression1`除以`expression2`，包括任何余数。  
  
 [\ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)返回整数商，将删除其余部分。  
  
## <a name="remarks"></a>备注  
 结果的数据类型取决于操作数的类型。 下表显示了如何确定结果的数据类型。  
  
|操作数数据类型|结果数据类型|  
|------------------------|----------------------|  
|这两个表达式是整数数据类型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)，[字节](../../../visual-basic/language-reference/data-types/byte-data-type.md)，[短](../../../visual-basic/language-reference/data-types/short-data-type.md)， [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)，[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)，[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)，[长](../../../visual-basic/language-reference/data-types/long-data-type.md)， [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|一个表达式是[单个](../../../visual-basic/language-reference/data-types/single-data-type.md)数据类型和其他不是[双精度](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|一个表达式是[十进制](../../../visual-basic/language-reference/data-types/decimal-data-type.md)数据类型和其他不是[单个](../../../visual-basic/language-reference/data-types/single-data-type.md)或[双精度](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|其中任何一个表达式是[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)数据类型|`Double`|  
  
 执行除法运算之前，将任何整数数值表达式被扩展为`Double`。 如果将结果分配到整数数据类型，请尝试将转换的结果 Visual Basic`Double`为该类型。 如果结果无法容纳在该类型，这可以引发异常。 具体而言，此帮助页上看到"尝试用零作除数"。  
  
 如果`expression1`或`expression2`的计算结果为[Nothing](../../../visual-basic/language-reference/nothing.md)，它将被视为零。  
  
## <a name="attempted-division-by-zero"></a>尝试的除数为零  
 如果`expression2`计算结果为零，`/`运算符在行为上以不同的方式不同操作数数据类型。 下表显示了可能的行为。  
  
|操作数数据类型|行为如果`expression2`为零|  
|------------------------|---------------------------------------|  
|浮点 (`Single`或`Double`)|返回无穷大 (<xref:System.Double.PositiveInfinity>或<xref:System.Double.NegativeInfinity>)，或<xref:System.Double.NaN>（而不是数字） 如果`expression1`也为零|  
|`Decimal`|将引发 <xref:System.DivideByZeroException>|  
|整型 （带符号或无符号）|尝试转换回整数类型，则会引发<xref:System.OverflowException>因为整型类型不能接受<xref:System.Double.PositiveInfinity>， <xref:System.Double.NegativeInfinity>，或 <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。 如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 此示例使用`/`运算符执行浮点除法。 结果是两个操作数的商。  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 在前面的示例表达式返回值为 2.5 3.333333。 请注意，结果始终是浮点 (`Double`)，即使这两个操作数都是整数常量。  
  
## <a name="see-also"></a>请参阅

- [/ = 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [运算符结果的数据类型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [算术运算符](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic 中的运算符优先级](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [按功能列出的运算符](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [在 Visual Basic 中的算术运算符](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
