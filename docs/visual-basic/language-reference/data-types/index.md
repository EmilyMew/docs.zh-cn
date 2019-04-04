---
title: 数据类型摘要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
ms.openlocfilehash: 29e5cbe09026dd52811c6c5fb88e940b45b7c0bb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821967"
---
# <a name="data-type-summary-visual-basic"></a>数据类型摘要 (Visual Basic)
下表显示了 Visual Basic 数据类型、 其支持的公共语言运行时类型、 他们的名义存储分配和其值的范围。  
  
|Visual Basic 类型|公共语言运行时类型结构|名义存储分配|取值范围|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|取决于实现平台|`True` 或 `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 个字节|0 到 255 （无符号）|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) （单个字符）|<xref:System.Char>|2 个字节|0 到 65535 （无符号）|  
|[Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 个字节|0:00:00 （午夜） 上 0001 到 9999 年 12 月 31 日晚上 11:59:59 年 1 月 1 日|  
|[小数](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 个字节|0 到 + 79228162514264337593543950335 / (+ /-7.9...E + 28) <sup>†</sup>没有小数点; 0 到 + /-7.9228162514264337593543950335 有 28 位小数; 右侧的位数<br /><br /> 最小非零数为 + / （+ /-1E 28)-0.0000000000000000000000000001 <sup>†</sup>|  
|[双精度](../../../visual-basic/language-reference/data-types/double-data-type.md)（双精度浮点）|<xref:System.Double>|8 个字节|-1.79769313486231570 e + 308 到-4.94065645841246544 e-324 <sup>†</sup>对于负值;<br /><br /> 4.94065645841246544 e-324 到 1.79769313486231570 e + 308 <sup>†</sup>对于正值|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 个字节|-2147483648 到 2147483647 （有符号）|  
|[长](../../../visual-basic/language-reference/data-types/long-data-type.md)（长整型）|<xref:System.Int64>|8 个字节|-9223372036854775808 到 9,223,372,036,854,775,807 (9.2...E + 18 <sup>†</sup>) （有符号）|  
|[Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> （类）|在 32 位平台上的 4 个字节<br /><br /> 在 64 位平台上的 8 个字节|任何类型可以存储在类型的变量 `Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 个字节|-128 到 127 （有符号）|  
|[短](../../../visual-basic/language-reference/data-types/short-data-type.md)（短整数）|<xref:System.Int16>|2 个字节|-32,768 到 32,767 （有符号）|  
|[单个](../../../visual-basic/language-reference/data-types/single-data-type.md)（单精度浮点）|<xref:System.Single>|4 个字节|-3.4028235E + 38 到-1.401298E-45 <sup>†</sup>对于负值;<br /><br /> 1.401298E-45 到 3.4028235E + 38 <sup>†</sup>对于正值|  
|[字符串](../../../visual-basic/language-reference/data-types/string-data-type.md)（可变长度）|<xref:System.String> （类）|取决于实现平台|0 到大约 2 亿个 Unicode 字符|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 个字节|0 到 4294967295 （无符号）|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 个字节|0 到 18446744073709551615 (1.8...E + 19 <sup>†</sup>) （无符号）|  
|[用户定义](../../../visual-basic/language-reference/data-types/user-defined-data-type.md)（结构）|(继承自<xref:System.ValueType>)|取决于实现平台|结构中的每个成员都有决定其数据类型，并独立于其他成员的范围|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 个字节|0 到 65,535 （无符号）|  
  
 <sup>†</sup>中*科学记数法*，"E"是指 10 的幂。 因此 3.56 e + 2 表示 3.56 x 10<sup>2</sup>或耗时 356，和 3.56 e-2 表示 3.56 / 10<sup>2</sup>或 0.0356。  
  
> [!NOTE]
>  对于包含文本的字符串，请使用<xref:Microsoft.VisualBasic.Strings.StrConv%2A>函数将从一个文本格式转换为另一个。  
  
 除了在声明语句中指定的数据类型，可以通过使用类型字符强制某些编程元素的数据类型。 请参阅[键入字符](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)。  
  
## <a name="memory-consumption"></a>内存消耗  
 声明基本数据类型时，是不安全假设其内存使用量，并以其名义存储分配相同。 这是由于以下注意事项：  
  
-   **存储分配。** 公共语言运行时可以将基于当前在其执行应用程序平台的特征的存储。 如果内存几乎已满，它可能会一起尽可能包尽可能真实地将声明的元素。 在其他情况下，可能会符合其内存地址与自然硬件边界，以优化性能。  
  
-   **平台宽度。** 在 64 位平台上的存储分配是不同的 32 位平台上的分配。  
  
### <a name="composite-data-types"></a>复合数据类型  
 相同的注意事项适用于复合数据类型，如结构或数组的每个成员。 不能依赖于只需将该类型的成员的名义存储分配相加。 此外，还有其他注意事项，如下所示：  
  
-   **开销。** 某些复合类型具有更多的内存要求。 例如，一个数组，使用额外的内存，数组本身，还为每个维度。 在 32 位平台上，这种开销当前是 12 个字节加上每个维度的 8 个字节。 在 64 位平台上此要求是增加一倍。  
  
-   **存储数据布局。** 不能完全假定已在内存中存储的顺序声明的顺序相同。 您甚至不能使假设字节对齐方式，例如 2 字节或 4 字节边界。 如果您在定义类或结构，并且您需要控制其成员的存储布局，可以将应用<xref:System.Runtime.InteropServices.StructLayoutAttribute>类或结构的属性。  
  
### <a name="object-overhead"></a>对象的开销  
 `Object`指任何基本或复合数据类型使用 4 个字节，以及数据类型中包含的数据。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [类型字符](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
