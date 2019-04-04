---
title: Single 数据类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: b90fdb562f9d65858ac477321a18067cc6e621a2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833297"
---
# <a name="single-data-type-visual-basic"></a>Single 数据类型 (Visual Basic)
保存有符号 IEEE 32 位 （4 字节） 单精度浮点数，值范围从-3.4028235E + 38 到-1.401298E-45 负值，从 1.401298E-45 到 3.4028235E + 38 对于正值。 单精度的数字存储一个实数的近似值。  
  
## <a name="remarks"></a>备注  
 使用`Single`数据类型包含不需要的完整数据宽度的浮点值`Double`。 在某些情况下，公共语言运行时可能地打包你`Single`变量紧密合作，以节省内存消耗。  
  
 `Single` 的默认值为 0。  
  
## <a name="programming-tips"></a>编程提示  
  
-   **精度。** 当使用浮点数时，请注意在内存中不一定有精确的表示形式。 这可能导致意外的结果从某些操作，如值比较和`Mod`运算符。 有关详细信息，请参阅[故障排除数据类型](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
-   **扩大转换。** `Single`数据类型加宽到`Double`。 这意味着可以将转换`Single`到`Double`而不会遇到<xref:System.OverflowException?displayProperty=nameWithType>错误。  
  
-   **尾随零。** 浮点数据类型不具有尾随 0 个字符的任何内部表示形式。 例如，它们不区分 4.2000 和 4.2。 因此，在显示或打印浮点值时不显示尾随 0 个字符。  
  
-   **类型字符。** 将文本类型字符 `F` 追加到文本会将其强制转换为 `Single` 数据类型。 将标识符类型字符 `!` 追加到任何标识符会将其强制转换为 `Single`。  
  
-   **Framework 类型。** .NET Framework 中的对应类型是 <xref:System.Single?displayProperty=nameWithType> 结构。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Single?displayProperty=nameWithType>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal 数据类型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Double 数据类型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [数据类型疑难解答](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
