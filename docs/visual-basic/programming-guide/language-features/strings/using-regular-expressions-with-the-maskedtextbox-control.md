---
title: 在 MaskedTextBox 控件中使用正则表达式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: e0165fb8d573878ae19378b2656d89627680b804
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826727"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>在 MaskedTextBox 控件中使用正则表达式 (Visual Basic)
此示例演示如何将简单的正则表达式以使用<xref:System.Windows.Forms.MaskedTextBox>控件。  
  
## <a name="description-of-the-masking-language"></a>屏蔽语言的描述  
 标准<xref:System.Windows.Forms.MaskedTextBox>屏蔽语言基于使用的那个`Masked Edit`控制在 Visual Basic 6.0 中，并且应该熟悉该平台中迁移的用户。  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>属性的<xref:System.Windows.Forms.MaskedTextBox>控件指定要使用哪些输入的掩码。 掩码必须是组成一个或多个掩码元素下表中的字符串。  
  
|屏蔽元素|描述|正则表达式元素|  
|---------------------|-----------------|--------------------------------|  
|0|介于 0 到 9 之间的任何单个数字。 必填条目。|\d|  
|9|数字或空格。 可选项。|[ \d]?|  
|#|数字或空格。 可选项。 如果此位置留空掩码中，它将呈现为一个空格。 加号 （+） 和减号 （-） 允许符号。|[ \d+-]?|  
|L|ASCII 字母。 必填条目。|[a-zA-Z]|  
|?|ASCII 字母。 可选项。|[a-zA-Z]?|  
|&|字符。 必填条目。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|字符。 可选项。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|包含当前请求的 URL 的|字母数字。 可选项。|\W|  
|.|相应于区域性的小数点占位符。|不可用。|  
|,|数千个适合区域性的占位符。|不可用。|  
|:|相应于区域性的时间分隔符。|不可用。|  
|/|相应于区域性的日期分隔符。|不可用。|  
|$|相应于区域性的货币符号。|不可用。|  
|\<|将转换为小写后面的所有字符。|不可用。|  
|>|将转换为大写后面的所有字符。|不可用。|  
|&#124;|撤消上一 shift 向上或向下移动。|不可用。|  
|&#92;|掩码字符，将其转换为文本进行转义。 "\\\\"是一个反斜杠的转义序列。|&#92;|  
|所有其他字符。|原义字符。 所有非掩码元素将显示为本身内<xref:System.Windows.Forms.MaskedTextBox>。|所有其他字符。|  
  
 小数点 （.）、 千分之几秒 （，）、 时间 （:）、 （/）、 日期和货币 （$） 符号默认为显示这些符号定义的应用程序的区域性。 还可以强制使用显示另一个区域性的符号<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>属性。  
  
## <a name="regular-expressions-and-masks"></a>正则表达式和蒙板  
 尽管可以使用正则表达式和掩码来验证用户输入，但它们并不完全相同。 正则表达式可以表达更复杂的模式比掩码，但更简洁、 区域相关的格式中，掩码可以表示相同的信息。  
  
 下表比较每个四个正则表达式和等效的掩码。  
  
|正则表达式|掩码|说明|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`掩码中的字符是一个逻辑日期分隔符，并且它将向用户显示为适用于应用程序的当前区域性的日期分隔符。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|在其中三个字母的月份缩写大写首字母后跟两个小写字母与美国格式的日期 （日、 月缩写和年）。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|美国电话号码，可选的区域代码。 如果用户不希望输入的可选字符，她可以输入空格，或者将鼠标指针放直接由第一个 0 表示掩码中的位置。|  
|`$\d{6}.00`|`$999,999.00`|0 到 999999 的范围中的货币值。 货币、 千分位的十进制字符将替换和在运行时与它们特定于区域性的等效项。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [在 Visual Basic 中验证字符串](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox 控件](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
