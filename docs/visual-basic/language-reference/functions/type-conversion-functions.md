---
title: 类型转换函数 (Visual Basic)
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 2b750f41343a4a68e29af6055815efd1e6470252
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816260"
---
# <a name="type-conversion-functions-visual-basic"></a>类型转换函数 (Visual Basic)
这些函数是代码的内联方式编译，这意味着转换代码计算表达式的值的一部分。 有时是没有调用过程，以完成转换，从而提高性能。 每个函数都强制转换为特定的数据类型的表达式。  
  
## <a name="syntax"></a>语法  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## <a name="part"></a>部件  
 `expression`  
 必需。 源数据类型的任何表达式。  
  
## <a name="return-value-data-type"></a>返回值的数据类型  
 下表中所示，函数名称确定它返回的值的数据类型。  
  
|功能名称|返回数据类型|为范围`expression`参数|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean 数据类型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任何有效`Char`或`String`或数值表达式。|  
|`CByte`|[Byte 数据类型](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) 通过<xref:System.Byte.MaxValue?displayProperty=nameWithType>(255) （无符号）; 小数部分舍入。<sup>1</sup><br/><br/>从 Visual Basic 15.8 开始，Visual Basic 可优化的性能与字节转换为浮点`CByte`函数; 请参阅[备注](#remarks)部分，了解详细信息。 请参阅[CInt 示例](#cint-example)有关示例。|  
|`CChar`|[Char 数据类型](../../../visual-basic/language-reference/data-types/char-data-type.md)|任何有效`Char`或`String`表达式; 仅第一个字符的`String`转换; 值可以是 0 到 65535 （无符号）。|  
|`CDate`|[Date 数据类型](../../../visual-basic/language-reference/data-types/date-data-type.md)|日期和时间的任何有效表示形式。|  
|`CDbl`|[Double 数据类型](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570 e + 308 到-4.94065645841246544 e-324 对于负值;4.94065645841246544 e-324 到 1.79769313486231570 e + 308 的正值。|  
|`CDec`|[Decimal 数据类型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+ /-79228162514264337593543950335 为零的数字，即，没有小数位的数字。 对于具有 28 位小数的数字，范围为 + /--7.9228162514264337593543950335 之间。 最小可能的非零数字为 0.0000000000000000000000000001 （+ /-1E 28)。|  
|`CInt`|[Integer 数据类型](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) 通过<xref:System.Int32.MaxValue?displayProperty=nameWithType>(2,147,483,647); 小数部分舍入。<sup>1</sup> <br/><br/>从 Visual Basic 15.8 开始，Visual Basic 可优化的性能与整数转换为浮点`CInt`函数; 请参阅[备注](#remarks)部分，了解详细信息。 请参阅[CInt 示例](#cint-example)有关示例。 |  
|`CLng`|[Long 数据类型](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-9223372036854775808) 通过<xref:System.Int64.MaxValue?displayProperty=nameWithType>(9,223,372,036,854,775,807); 小数部分舍入。<sup>1</sup><br/><br/>从 Visual Basic 15.8 开始，Visual Basic 可优化的性能与 64 位整数转换为浮点`CLng`函数; 请参阅[备注](#remarks)部分，了解详细信息。 请参阅[CInt 示例](#cint-example)有关示例。|  
|`CObj`|[Object 数据类型](../../../visual-basic/language-reference/data-types/object-data-type.md)|任何有效表达式。|  
|`CSByte`|[SByte 数据类型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) 通过<xref:System.SByte.MaxValue?displayProperty=nameWithType>(127); 小数部分舍入。<sup>1</sup><br/><br/>从 Visual Basic 15.8 开始，Visual Basic 来优化性能的使用的有符号的字节转换为浮点`CSByte`函数; 请参阅[备注](#remarks)部分，了解详细信息。 请参阅[CInt 示例](#cint-example)有关示例。|  
|`CShort`|[Short 数据类型](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) 通过<xref:System.Int16.MaxValue?displayProperty=nameWithType>(32,767); 小数部分舍入。<sup>1</sup><br/><br/>从 Visual Basic 15.8 开始，Visual Basic 来优化性能的使用 16 位整数转换为浮点`CShort`函数; 请参阅[备注](#remarks)部分，了解详细信息。 请参阅[CInt 示例](#cint-example)有关示例。|  
|`CSng`|[Single 数据类型](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823e+38 到-1.401298E-45 对于负值;1.401298E-45 到 3.402823e+38 对于正值。|  
|`CStr`|[String 数据类型](../../../visual-basic/language-reference/data-types/string-data-type.md)|返回有关`CStr`依赖于`expression`参数。 请参阅[CStr 函数的返回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。|  
|`CUInt`|[UInteger 数据类型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) 通过<xref:System.UInt32.MaxValue?displayProperty=nameWithType>(4,294,967,295) （无符号）; 小数部分舍入。<sup>1</sup><br/><br/>从 Visual Basic 15.8 开始，Visual Basic 可优化的性能与无符号的整数转换为浮点`CUInt`函数; 请参阅[备注](#remarks)部分，了解详细信息。 请参阅[CInt 示例](#cint-example)有关示例。|  
|`CULng`|[ULong 数据类型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) 通过<xref:System.UInt64.MaxValue?displayProperty=nameWithType>(18446744073709551615) （无符号）; 小数部分舍入。<sup>1</sup><br/><br/>从 Visual Basic 15.8 开始，Visual Basic 可优化的性能与无符号长整数转换为浮点`CULng`函数; 请参阅[备注](#remarks)部分，了解详细信息。 请参阅[CInt 示例](#cint-example)有关示例。|  
|`CUShort`|[UShort 数据类型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) 通过<xref:System.UInt16.MaxValue?displayProperty=nameWithType>(65535) （无符号）; 小数部分舍入。<sup>1</sup><br/><br/>从 Visual Basic 15.8 开始，Visual Basic 来优化性能的使用 16 位无符号的整数转换为浮点`CUShort`函数; 请参阅[备注](#remarks)部分，了解详细信息。 请参阅[CInt 示例](#cint-example)有关示例。|  
  
 <sup>1</sup>小数部分时可能会出现一种特殊的舍入名为*银行家的舍入*。 有关详细信息，请参阅"备注"。  
  
## <a name="remarks"></a>备注  
 通常，您应使用 Visual Basic 类型转换函数优先于.NET Framework 方法如`ToString()`，而是在<xref:System.Convert>类或各个类型结构或类上。 Visual Basic 函数设计为与 Visual Basic 代码的最佳交互，并且它们还使得更短且更易于阅读源代码。 此外，.NET Framework 转换方法不始终生成与 Visual Basic 函数，例如，在转换时相同的结果`Boolean`到`Integer`。 有关详细信息，请参阅[故障排除数据类型](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  


从 Visual Basic 15.8 开始，浮点 point 到整数的转换的性能优化时将传递<xref:System.Single>或<xref:System.Double>返回值通过下列方法之一的整数转换函数 (`CByte`， `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

这种优化允许代码执行大量的整数转换为两倍的速度运行。 下面的示例说明了这些优化浮点 point 到整数转换：

```vb
Dim s As Single = 173.7619
Dim d As Double = s 

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a>行为  
  
-   **强制转换。** 一般情况下，可以使用数据类型转换函数要强制转换到特定的数据类型，而不是默认数据类型操作的结果。 例如，使用`CDec`强制执行在其中单精度、 双精度或整型运算将通常会发生的情况下小数运算。  
  
-   **失败的转换。** 如果`expression`传递给函数是外部的数据类型范围它是要转换<xref:System.OverflowException>时发生。  
  
-   **小数部分。** 当将非整型值转换为整型类型，整数转换函数 (`CByte`， `CInt`， `CLng`， `CSByte`， `CShort`， `CUInt`， `CULng`，和`CUShort`) 中删除小数部分和舍入到最接近的整数值。  
  
     如果小数部分正好是 0.5，整数转换函数将其舍入为接近的偶数。 例如，0.5 舍入为 0，和 1.5 和 2.5 舍入为 2。 这有时称为*银行家的舍入*，其目的是将许多这样的数字相加时可能会累积的偏补偿。  
  
     `CInt` 并`CLng`有所不同<xref:Microsoft.VisualBasic.Conversion.Int%2A>和<xref:Microsoft.VisualBasic.Conversion.Fix%2A>函数，它截断，而不是舍入的数字的小数部分。 此外，`Fix`和`Int`始终返回相同的数据类型的值与传入的。  
  
-   **日期/时间转换。** 使用<xref:Microsoft.VisualBasic.Information.IsDate%2A>函数来确定一个值，是否可以转换为日期和时间。 `CDate` 识别的日期文本和时间文本，但不是数字值。 转换 Visual Basic 6.0`Date`值设为`Date`在 Visual Basic 2005 中的值或更高版本，可以使用<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>方法。  
  
-   **非特定于日期/时间值。** [日期数据类型](../../../visual-basic/language-reference/data-types/date-data-type.md)始终包含日期和时间信息。 为进行类型转换，Visual Basic 将 1/1/0001 (年 1 月 1 年 1) 要*中性值*次为非特定值的日期，和 00:00:00 （午夜）。 如果您在转换`Date`值为一个字符串，`CStr`不在生成的字符串中包括非特定值。 例如，如果您将转换`#January 1, 0001 9:30:00#`为一个字符串，则结果为"9:30:00 AM"; 禁止显示日期信息。 但是，日期信息仍会在原始`Date`值和可恢复函数如<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>函数。  
  
-   **区域差异。** 涉及到字符串类型转换函数执行基于应用程序的当前区域性设置的转换。 例如，`CDate`识别根据您的系统的区域设置日期的格式。 必须提供一天、 月和年按正确的顺序为区域设置，或可能不正确解释日期。 如果它包含一个星期的字符串，例如"Wednesday"无法识别的长日期格式。  
  
     如果需要将转换为或格式不是由您的区域设置指定的值的字符串表示形式，则不能使用 Visual Basic 类型转换函数。 若要执行此操作，请使用`ToString(IFormatProvider)`和`Parse(String, IFormatProvider)`该值的类型的方法。 例如，使用<xref:System.Double.Parse%2A?displayProperty=nameWithType>转换为字符串时`Double`，并使用<xref:System.Double.ToString%2A?displayProperty=nameWithType>类型的值转换时`Double`为字符串。  
  
## <a name="ctype-function"></a>CType Function  
 [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md)采用第二个参数`typename`，并将强制`expression`到`typename`，其中`typename`可以是任何数据类型、 结构、 类或接口向其存在的有效转换。  
  
 有关的比较`CType`与其他类型转换关键字，请参阅[DirectCast 运算符](../../../visual-basic/language-reference/operators/directcast-operator.md)并[TryCast 运算符](../../../visual-basic/language-reference/operators/trycast-operator.md)。  
  
## <a name="cbool-example"></a>CBool 示例  
 下面的示例使用`CBool`函数将表达式转换为`Boolean`值。 如果表达式计算结果为非零值，`CBool`将返回`True`; 否则为它将返回`False`。  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a>CByte 示例  
 下面的示例使用`CByte`函数将转换为表达式`Byte`。  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a>CChar 示例  
 下面的示例使用`CChar`函数将转换的第一个字符`String`表达式`Char`类型。  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 输入的参数`CChar`的数据类型必须为`Char`或`String`。 不能使用`CChar`若要将数字转换为字符，因为`CChar`不能接受数值数据类型。 以下示例获取一个表示码位 （字符代码） 的数字，并将其转换为相应的字符。 它使用<xref:Microsoft.VisualBasic.Interaction.InputBox%2A>函数获取数字的字符串`CInt`要转换为类型字符串`Integer`，和`ChrW`要转换的编号，以键入`Char`。  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a>CDate 示例  
 下面的示例使用`CDate`函数将字符串转换为`Date`值。 一般情况下，不建议进行硬编码的日期和时间作为字符串 （如在此示例中所示）。 使用文字日期和时间文字，如 #Feb 12，1969 # 和 # 4:45:23 PM #，而是。  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a>CDbl 示例  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a>CDec 示例  
 下面的示例使用`CDec`函数将转换为数字值`Decimal`。  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a>CInt 示例  
 下面的示例使用`CInt`函数将值转换为`Integer`。  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a>CLng 示例
 下面的示例使用`CLng`函数以将值转换为`Long`。  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a>示例中的 CObj  
 下面的示例使用`CObj`函数将转换为数字值`Object`。 `Object`变量本身包含仅一个四字节的指针，用于指向`Double`分配给它的值。  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a>CSByte 示例  
 下面的示例使用`CSByte`函数将转换为数字值`SByte`。  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a>CShort 示例  
 下面的示例使用`CShort`函数将转换为数字值`Short`。  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a>CSng 示例  
 下面的示例使用`CSng`函数以将值转换为`Single`。  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a>CStr 示例  
 下面的示例使用`CStr`函数将转换为数字值`String`。  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 下面的示例使用`CStr`函数将转换`Date`值到`String`值。  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` 始终呈现`Date`采用当前区域设置，例如，标准的短格式的值"2003 年 6 月 15 日下午 4:35:47"。 但是，`CStr`禁止*中性值*1/1/0001 的日期和时间的 00:00:00。  
  
 有关详细信息返回的值`CStr`，请参阅[CStr 函数的返回值](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)。  
  
## <a name="cuint-example"></a>CUInt 示例  
 下面的示例使用`CUInt`函数将转换为数字值`UInteger`。  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a>CULng 示例  
 下面的示例使用`CULng`函数将转换为数字值`ULong`。  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a>CUShort 示例  
 下面的示例使用`CUShort`函数将转换为数字值`UShort`。  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [转换函数](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [在 Visual Basic 中的类型转换](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
