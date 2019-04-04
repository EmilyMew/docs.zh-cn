---
title: String 数据类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 3e87dc6527b4351467b1155439ee8266157c16ff
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842286"
---
# <a name="string-data-type-visual-basic"></a>String 数据类型 (Visual Basic)
存储无符号的 16 位 （2 个字节） 码位的序列该范围从 0 到 65535 之间的值中。 每个*代码点*，或字符代码，表示单个 Unicode 字符。 一个字符串，可包含从 0 到大约 20 亿 (2 ^31) 的 Unicode 字符。  
  
## <a name="remarks"></a>备注  
 使用`String`数据类型来保存多个字符，无需数组管理开销`Char()`，数组`Char`元素。  
  
 默认值`String`是`Nothing`（空引用）。 请注意，这并不相同，则为空字符串 (值`""`)。  
  
## <a name="unicode-characters"></a>Unicode 字符  
 Unicode 的第一个 128 个码位 (0-127) 对应的字母和标准的美式键盘上的符号。 这些第一个 128 个码位都与 ASCII 字符集定义相同。 第二个 128 个码位 (128-255) 表示特殊字符，如的基于拉丁文的字母、 重音符号、 货币符号和小数部分。 Unicode 使用各种各样的符号的其余代码点 (256-65535)。 这包括全球范围内的文本字符、 音调符号和数学和技术符号。  
  
 您可以使用方法，如<xref:System.Char.IsDigit%2A>并<xref:System.Char.IsPunctuation%2A>中的单个字符上`String`变量以确定其 Unicode 分类。  
  
## <a name="format-requirements"></a>格式要求  
 必须将`String`引号内的文本 (`" "`)。 如果为一个字符串中的字符，必须包含引号，则使用两个连续的引号 (`""`)。 下面的示例阐释了这一点。  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 请注意，连续的引号表示字符串中的引号都独立于引号开始和结束`String`文本。  
  
## <a name="string-manipulations"></a>字符串操作  
 分配到一个字符串后`String`变量，该字符串是*不可变*，这意味着您不能更改它的长度或内容。 在修改以任何方式的字符串时，Visual Basic 创建一个新字符串和放弃前一个。 `String`变量然后指向新的字符串。  
  
 您可以操作的内容`String`变量使用的各种字符串函数。 下面的示例演示<xref:Microsoft.VisualBasic.Strings.Left%2A>函数  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 可能会用前导或尾随空格填充通过另一个组件创建的字符串。 如果你收到此类字符串，则可以使用<xref:Microsoft.VisualBasic.Strings.Trim%2A>， <xref:Microsoft.VisualBasic.Strings.LTrim%2A>，和<xref:Microsoft.VisualBasic.Strings.RTrim%2A>函数来删除这些空格。  
  
 有关字符串操作的详细信息，请参阅[字符串](../../../visual-basic/programming-guide/language-features/strings/index.md)。  
  
## <a name="programming-tips"></a>编程提示  
  
-   **负号。** 请记住保留字符`String`是无符号，并且不能表示负值。 在任何情况下，不应使用`String`来保存数值。  
  
-   **互操作注意事项。** 如果你不是为.NET Framework 编写的组件与交互如自动化或 COM 对象，请记住，字符串字符具有不同的数据宽度 （8 位） 在其他环境中。 如果您将 8 位字符的字符串参数传递给此类组件，将其作为声明`Byte()`，数组`Byte`元素，而不是`String`中新的 Visual Basic 代码。  
  
-   **类型字符。** 追加标识符类型字符`$`到任何标识符会强制转换到`String`数据类型。 `String` 有没有文本类型字符。 但是，编译器将文本括在引号 (`" "`) 作为`String`。  
  
-   **Framework 类型。** .NET Framework 中的对应类型是<xref:System.String?displayProperty=nameWithType>类。  
  
## <a name="see-also"></a>请参阅

- <xref:System.String?displayProperty=nameWithType>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [Char 数据类型](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [如何：调用需要使用无符号类型的 Windows 函数](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
