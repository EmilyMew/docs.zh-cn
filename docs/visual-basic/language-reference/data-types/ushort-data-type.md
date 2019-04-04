---
title: UShort 数据类型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
ms.openlocfilehash: 8845a6bde4e1a701b5420029788259724cd0f8d9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829949"
---
# <a name="ushort-data-type-visual-basic"></a>UShort 数据类型 (Visual Basic)

包含无符号的 16 位 （2 个字节） 整数取值范围为 0 到 65,535。  
  
## <a name="remarks"></a>备注

 使用`UShort`数据类型来包含二进制数据太大， `Byte`。  
  
 `UShort` 的默认值为 0。  

## <a name="literal-assignments"></a>文本分配

您可以声明并初始化`UShort`变量由将其分配十进制文本、 十六进制文本八进制文本，或 （Visual Basic 从 2017年开始） 二进制文本。 如果整数文本在 `UShort` 范围之外（即，如果它小于 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大于 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>），会发生编译错误。

在以下示例中，整数等于 65034、 表示为十进制、 十六进制和二进制文本分配给`UShort`值。
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> 使用前缀`&h`或`&H`来表示十六进制文本前缀`&b`或`&B`来表示二进制文本和前缀`&o`或`&O`来表示八进制文本。 十进制文本没有前缀。

从 Visual Basic 2017 开始，你还可以使用下划线字符， `_`，作为数字分隔符，以增强可读性，如以下示例所示。

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

从 Visual Basic 15.5 开始，你还可以使用下划线字符 (`_`) 作为前缀和十六进制、 二进制或八进制数字之间的前导分隔符。 例如：

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

此外可以包含数值`US`或`us`[键入字符](../../programming-guide/language-features/data-types/type-characters.md)来表示`UShort`数据类型，如以下示例所示。

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a>编程提示
  
-   **负号。** 因为`UShort`是无符号的类型，它不能表示为负数。 如果使用一元负 (`-`) 运算符的表达式的计算结果为类型`UShort`，Visual Basic 将转换为表达式`Integer`第一个。  
  
-   **CLS 遵从性。** `UShort`数据类型不属于[公共语言规范](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)，因此符合 cls 的代码不能使用使用它的组件。
  
-   **扩大转换。** `UShort`数据类型加宽到`Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，和`Double`。 这意味着可以将转换`UShort`而不会遇到这些类型的任何<xref:System.OverflowException?displayProperty=nameWithType>错误。  
  
-   **类型字符。** 追加文本类型字符`US`为文本将其强制转换到`UShort`数据类型。 `UShort` 有没有标识符类型字符。  
  
-   **Framework 类型。** .NET Framework 中的对应类型是 <xref:System.UInt16?displayProperty=nameWithType> 结构。  
  
## <a name="see-also"></a>请参阅

- <xref:System.UInt16>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [如何：调用需要使用无符号类型的 Windows 函数](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
