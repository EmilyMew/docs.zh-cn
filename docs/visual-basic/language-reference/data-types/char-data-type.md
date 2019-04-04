---
title: Char 数据类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: b50c902f69f7602dbad4663dc35bf0a2b932973f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832081"
---
# <a name="char-data-type-visual-basic"></a>Char 数据类型 (Visual Basic)
保存无符号的 16 位 （2 个字节） 码位，取值范围为 0 到 65535 之间。 每个*代码点*，或字符代码，表示单个 Unicode 字符。  
  
## <a name="remarks"></a>备注  
 使用`Char`数据类型时需要保存只有一个字符且不需要的开销`String`。 在某些情况下可以使用`Char()`，数组`Char`元素，来保存多个字符。  
  
 默认值`Char`是字符其码位为 0。  
  
## <a name="unicode-characters"></a>Unicode 字符  
 Unicode 的第一个 128 个码位 (0-127) 对应的字母和标准的美式键盘上的符号。 这些第一个 128 个码位都与 ASCII 字符集定义相同。 第二个 128 个码位 (128-255) 表示特殊字符，如的基于拉丁文的字母、 重音符号、 货币符号和小数部分。 Unicode 使用各种各样的符号，包括全球范围内的文本字符、 音调符号和数学和技术符号的其余代码点 (256-65535)。  
  
 可以使用方法，如<xref:System.Char.IsDigit%2A>并<xref:System.Char.IsPunctuation%2A>上`Char`变量以确定其 Unicode 分类。  
  
## <a name="type-conversions"></a>类型转换  
 Visual Basic 不之间直接转换`Char`与数值类型。 可以使用<xref:Microsoft.VisualBasic.Strings.Asc%2A>或<xref:Microsoft.VisualBasic.Strings.AscW%2A>函数将转换`Char`值设为`Integer`表示其码位。 可以使用<xref:Microsoft.VisualBasic.Strings.Chr%2A>或<xref:Microsoft.VisualBasic.Strings.ChrW%2A>函数将转换`Integer`值设为`Char`具有该码位。  
  
 如果类型检查开关 ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) 处于打开状态，必须将文本类型字符附加到单字符字符串文本以标识为`Char`数据类型。 下面的示例阐释了这一点。  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>编程提示  
  
-   **负号。** `Char` 是一个无符号的类型，不能表示为负值。 在任何情况下，不应使用`Char`来保存数值。  
  
-   **互操作注意事项。** 如果不是为.NET Framework 编写的组件接口如自动化或 COM 对象，请记住，字符类型具有不同的数据宽度 (8 bits) 在其他环境中。 如果将 8 位自变量传递给此类组件中时，将其作为声明`Byte`而不是`Char`中新的 Visual Basic 代码。  
  
-   **扩大转换。** `Char`数据类型加宽到`String`。 这意味着可以将转换`Char`到`String`而不会遇到<xref:System.OverflowException?displayProperty=nameWithType>错误。  
  
-   **类型字符。** 追加文本类型字符`C`到单字符字符串文本将其强制转换到`Char`数据类型。 `Char` 有没有标识符类型字符。  
  
-   **Framework 类型。** .NET Framework 中的对应类型是 <xref:System.Char?displayProperty=nameWithType> 结构。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [String 数据类型](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [如何：调用需要使用无符号类型的 Windows 函数](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
