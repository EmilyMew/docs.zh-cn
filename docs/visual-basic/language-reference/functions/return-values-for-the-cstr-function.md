---
title: 返回 CStr 函数的值 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- times [Visual Basic], CStr Function return values
- type conversion [Visual Basic]
- dates [Visual Basic], CStr Function return values
- CStr function
- strings [Visual Basic], return value
- Date data type [Visual Basic], converting
- dates [Visual Basic]
- String data type [Visual Basic], converting
ms.assetid: 3aa744e7-1419-45d5-85e3-e5abc2953673
ms.openlocfilehash: 3653194c7e48533e664ac7513ca7f4f48d1c69f7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819510"
---
# <a name="return-values-for-the-cstr-function-visual-basic"></a>返回 CStr 函数的值 (Visual Basic)
下表介绍的返回值`CStr`为不同的数据类型的`expression`。  
  
|如果`expression`类型是|`CStr` 返回|  
|-----------------------------|--------------------|  
|[Boolean 数据类型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|包含"True"或者"False"。|  
|[Date 数据类型](../../../visual-basic/language-reference/data-types/date-data-type.md)|一个字符串，包含`Date`系统的短日期格式的值 （日期和时间）。|  
|[数值数据类型](../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)|表示数字的字符串。|  
  
## <a name="cstr-and-date"></a>CStr 和日期  
 `Date`类型始终包含日期和时间信息。 为进行类型转换，Visual Basic 将 1/1/0001 (年 1 月 1 年 1) 要*中性值*次为非特定值的日期，和 00:00:00 （午夜）。 `CStr` 不在生成的字符串中包括非特定值。 例如，如果您将转换`#January 1, 0001 9:30:00#`为一个字符串，则结果为"9:30:00 AM"; 禁止显示日期信息。 但是，日期信息仍会在原始`Date`值和可恢复函数如<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>。  
  
> [!NOTE]
>  `CStr`函数不执行基于应用程序的当前区域性设置其转换。 若要获取特定区域性中的数字的字符串表示形式，请使用数字的`ToString(IFormatProvider)`方法。 例如，使用<xref:System.Double.ToString%2A?displayProperty=nameWithType>类型的值转换时`Double`到`String`。  
  
## <a name="see-also"></a>请参阅

- <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>
- [类型转换函数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Boolean 数据类型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [Date 数据类型](../../../visual-basic/language-reference/data-types/date-data-type.md)
