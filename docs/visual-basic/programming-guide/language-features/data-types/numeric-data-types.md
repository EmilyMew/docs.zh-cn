---
title: 数值型数据类型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: 75e60cb2a3a934956099ce6fc7d81bf6ecea4d11
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841636"
---
# <a name="numeric-data-types-visual-basic"></a>数值型数据类型 (Visual Basic)
Visual Basic 提供若干*数值数据类型*来处理各种表示形式中的数字。 *整型*类型表示仅整数 （正数、 负数和零），并*nonintegral*类型具有整数和小数部分表示的数字。  
  
 显示 Visual Basic 数据类型的并排比较的表，请参阅[数据类型](../../../../visual-basic/language-reference/data-types/index.md)。  
  
## <a name="integral-numeric-types"></a>整型数值类型  
 *整数数据类型*是表示没有小数部分的唯一数字。  
  
 *签名*整型数据类型[SByte 数据类型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)（8 位）、 [Short 数据类型](../../../../visual-basic/language-reference/data-types/short-data-type.md)（16 位），[整数数据类型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)（32-位） 和[Long 数据类型](../../../../visual-basic/language-reference/data-types/long-data-type.md)（64 位）。 如果某个变量始终存储整数而不是小数数字，其声明为以下类型之一。  
  
 *无符号*整型类型包括[Byte 数据类型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)（8 位）、 [UShort 数据类型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)（16 位）， [UInteger 数据类型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)（32-位） 和[ULong 数据类型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)（64 位）。 如果变量包含二进制数据或未知种类的数据，请将其作为其中一种类型声明。  
  
### <a name="performance"></a>性能  
 更快地比其他数据类型的整型类型算术运算。 它们是使用最快`Integer`和`UInteger`Visual Basic 中的类型。  
  
### <a name="large-integers"></a>大整数  
 如果你需要保存整数大于`Integer`数据类型可以容纳，则可以使用`Long`数据类型。 `Long` 变量可以存储从-9223372036854775808 到 9,223,372,036,854,775,807 的数字。 使用操作`Long`时速度稍慢比使用`Integer`。  
  
 如果需要更大的值，则可以使用[十进制数据类型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)。 可以存储从-79228162514264337593543950335 到 79228162514264337593543950335 中数字`Decimal`变量，如果不使用任何小数位数。 但是，使用操作`Decimal`数字是显著变慢于与其他任何数字数据类型。  
  
### <a name="small-integers"></a>小整数  
 如果不需要的全部`Integer`数据类型，则可以使用`Short`数据类型，它包含从-32,768 到 32767 之间的整数。 对于最小的整数范围，`SByte`数据类型可存放从-128 到 127 的整数。 如果您有大量的变量包含小整数，公共语言运行时可以有时存储你`Short`和`SByte`变量更有效地，以节省内存消耗。 但是，与 operations`Short`并`SByte`比使用稍有些慢`Integer`。  
  
### <a name="unsigned-integers"></a>无符号的整数  
 如果您知道您的变量永远不需要保存为负数，则可以使用*无符号类型*`Byte`， `UShort`， `UInteger`，并`ULong`。 每种数据类型可以存储的正整数两次大小的相应的有符号类型 (`SByte`， `Short`， `Integer`，和`Long`)。 就性能来说，每个无符号的类型是完全不如其相应的有符号类型。 具体而言，`UInteger`与共享`Integer`最有效的所有基本数值数据类型的区别。  
  
## <a name="nonintegral-numeric-types"></a>非整型数值类型  
 *非整型数据类型*是表示整数和小数部分的数字。  
  
 非整型数值数据类型为`Decimal`（128 位定点）[单一数据类型](../../../../visual-basic/language-reference/data-types/single-data-type.md)（32 位浮点） 和[双精度数据类型](../../../../visual-basic/language-reference/data-types/double-data-type.md)（64 位浮点数）。 它们已全部签名的类型。 如果一个变量可以包含一小部分，将其声明为以下类型之一。  
  
 `Decimal` 不是浮点数据类型。 `Decimal` 数字具有的二进制整数值和一个指定的值的哪些部分是小数部分的整数比例因子。  
  
 可以使用`Decimal`对于货币值的变量。 优点是值的精度。 `Double`数据类型更快，且需要较少的内存，但很容易产生舍入错误。 `Decimal`数据类型将保留完整精度为 28 位小数。  
  
 浮点 (`Single`并`Double`) 数字有更大范围比`Decimal`数字，但可能会出现舍入误差。 浮点类型支持比有效位减少`Decimal`，但可以表示更大的值。  
  
 非整型数值可以表示为 mmmEeee，在该 mmm*尾数*（有效位） 并且 eee*指数*（10 的幂）。 非整型类型的最高的正数值才为 7.9228162514264337593543950335 e + 28 `Decimal`，为 3.4028235E + 38 `Single`，和 1.79769313486231570 e + 308 `Double`。  
  
### <a name="performance"></a>性能  
 `Double` 因为在当前平台上的处理器执行以双精度浮点运算，则是最有效的小数数据类型。 但是，与 operations`Double`不是与整型类型，如一样快`Integer`。  
  
### <a name="small-magnitudes"></a>较小的量值  
 对于具有可能的最小大小 （接近 0），数字`Double`变量可以存储数字小-4.94065645841246544-324 负值和最大 4.94065645841246544 e-324 的正值。  
  
### <a name="small-fractional-numbers"></a>小小数位的数字  
 如果不需要的全部`Double`数据类型，则可以使用`Single`数据类型，它包含从-3.4028235E + 38 到 3.4028235E + 38 浮点数。 最小最小量值为`Single`变量是-1.401298E-45 为负值，1.401298E-45 对于正值。 如果您有非常大量的变量，用于保存小的浮点数，公共语言运行时有时可以存储在`Single`变量更有效地，以节省内存消耗。  
  
## <a name="see-also"></a>请参阅

- [基本数据类型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [字符数据类型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [杂项数据类型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [数据类型疑难解答](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：调用需要使用无符号类型的 Windows 函数](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
