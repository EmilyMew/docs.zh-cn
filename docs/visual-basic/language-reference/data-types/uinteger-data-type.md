---
title: UInteger 数据类型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: 4d93b1e40371b00f9d1ff69ec31ad0983beb493f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821486"
---
# <a name="uinteger-data-type"></a>UInteger 数据类型

包含无符号的 32 位 （4 字节） 整数取值范围为 0 到 4294967295。  
  
## <a name="remarks"></a>备注

 `UInteger`数据类型提供了最有效的数据宽度的最大无符号的值。  
  
 `UInteger` 的默认值为 0。  
  
## <a name="literal-assignments"></a>文本分配

您可以声明并初始化`UInteger`变量由将其分配十进制文本、 十六进制文本八进制文本，或 （Visual Basic 从 2017年开始） 二进制文本。 如果整数文本在 `UInteger` 范围之外（即，如果它小于 <xref:System.UInt32.MinValue?displayProperty=nameWithType> 或大于 <xref:System.UInt32.MaxValue?displayProperty=nameWithType>），会发生编译错误。

在以下示例中，表示为十进制、十六进制和二进制文本且等于 3,000,000,000 的整数被分配给 `UInteger` 值。
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> 使用前缀`&h`或`&H`来表示十六进制文本前缀`&b`或`&B`来表示二进制文本和前缀`&o`或`&O`来表示八进制文本。 十进制文本没有前缀。

从 Visual Basic 2017 开始，你还可以使用下划线字符， `_`，作为数字分隔符，以增强可读性，如以下示例所示。

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

从 Visual Basic 15.5 开始，你还可以使用下划线字符 (`_`) 作为前缀和十六进制、 二进制或八进制数字之间的前导分隔符。 例如：

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

此外可以包含数值`UI`或`ui`[键入字符](../../programming-guide/language-features/data-types/type-characters.md)来表示`UInteger`数据类型，如以下示例所示。

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>编程提示

 `UInteger`并`Integer`数据类型在 32 位处理器上，提供最佳性能，因为较小的整数类型 (`UShort`， `Short`， `Byte`，并`SByte`)，即使它们使用较少的位，需要更多的时间加载、 存储和提取。  
  
-   **负号。** 因为`UInteger`是无符号的类型，它不能表示为负数。 如果使用一元负 (`-`) 运算符的表达式的计算结果为类型`UInteger`，Visual Basic 将转换为表达式`Long`第一个。  
  
-   **CLS 遵从性。** `UInteger`数据类型不属于[公共语言规范](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)，因此符合 cls 的代码不能使用使用它的组件。
  
-   **互操作注意事项。** 如果你与不是为.NET Framework 中，如自动化或 COM 对象，编写组件交互请记住，类型，如`uint`可以在其他环境中具有不同的数据宽度 （16 位）。 如果您将 16 位自变量传递给此类组件，将其作为声明`UShort`而不是`UInteger`中托管的 Visual Basic 代码。  
  
-   **扩大转换。** `UInteger`数据类型加宽到`Long`， `ULong`， `Decimal`， `Single`，并`Double`。 这意味着可以将转换`UInteger`而不会遇到这些类型的任何<xref:System.OverflowException?displayProperty=nameWithType>错误。  
  
-   **类型字符。** 追加文本类型字符`UI`为文本将其强制转换到`UInteger`数据类型。 `UInteger` 有没有标识符类型字符。  
  
-   **Framework 类型。** .NET Framework 中的对应类型是 <xref:System.UInt32?displayProperty=nameWithType> 结构。  
  
## <a name="see-also"></a>请参阅

- <xref:System.UInt32>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [如何：调用需要使用无符号类型的 Windows 函数](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
