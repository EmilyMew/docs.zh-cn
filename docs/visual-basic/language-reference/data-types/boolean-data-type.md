---
title: Boolean 数据类型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 7b64302d801a08f976de0ec969983c821f7a8471
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841209"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean 数据类型 (Visual Basic)
可以仅由值保存`True`或`False`。 关键字`True`并`False`对应的两种状态`Boolean`变量。  
  
## <a name="remarks"></a>备注  
 使用[布尔数据类型 (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md)是/否或开/关包含两个状态的值，如 true/false。  
  
 `Boolean` 的默认值为 `False`。  
  
 `Boolean` 值不存储为数字，并存储的值并不等同于数字。 绝不应编写依赖于等效的数值的代码`True`和`False`。 只要有可能，应限制的使用情况`Boolean`它们设计的逻辑值的变量。  
  
## <a name="type-conversions"></a>类型转换  
 当 Visual Basic 将转换为数值数据类型值`Boolean`，将 0 变为`False`和所有其他值将成为`True`。 当 Visual Basic 转换`Boolean`值为数值类型，`False`变为 0 和`True`变得为-1。  
  
 之间转换时`Boolean`值和数值数据类型，请记住，.NET Framework 转换方法不始终生成与 Visual Basic 转换关键字相同的结果。 这是因为 Visual Basic 转换可以保留行为与早期版本兼容。 有关详细信息，请参阅"布尔值类型不会不转换到数值类型准确"中[故障排除数据类型](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)。  
  
## <a name="programming-tips"></a>编程提示  
  
-   **负号。** `Boolean` 不是数值类型，不能表示为负值。 在任何情况下，不应使用`Boolean`来保存数值。  
  
-   **类型字符。** `Boolean` 不包含文本类型字符或标识符类型字符。  
  
-   **Framework 类型。** .NET Framework 中的对应类型是 <xref:System.Boolean?displayProperty=nameWithType> 结构。  
  
## <a name="example"></a>示例  
 在以下示例中，`runningVB`是`Boolean`变量，其中存储一个简单的是/否设置。  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Boolean?displayProperty=nameWithType>
- [数据类型](../../../visual-basic/language-reference/data-types/index.md)
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [转换摘要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [有效使用数据类型](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [数据类型疑难解答](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType 函数](../../../visual-basic/language-reference/functions/ctype-function.md)
