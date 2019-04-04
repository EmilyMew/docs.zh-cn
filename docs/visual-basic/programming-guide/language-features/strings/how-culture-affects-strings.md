---
title: 区域性对字符串的影响 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
ms.openlocfilehash: d3c7ae9da9c18e53da393928e34dcfbf04fc891c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834616"
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>区域性对字符串的影响 (Visual Basic)
此帮助页讨论了 Visual Basic 如何使用区域性信息来执行的字符串转换和比较。  
  
## <a name="when-to-use-culture-specific-strings"></a>何时使用特定于区域性的字符串  
 通常情况下，应使用特定于区域性的字符串的所有数据提供给和阅读用户，并对应用程序的内部数据使用固定区域性的字符串。  
  
 例如，如果你的应用程序要求用户以字符串形式输入日期，应预计到用户根据其区域性字符串的格式和应用程序应适当地转换字符串。 如果您的应用程序然后显示该日期在其用户界面中的，它应用户的区域性中呈现它。  
  
 但是，如果应用程序上载到中心服务器的日期，它应格式根据一个特定区域性，以防止产生混乱之间可能不同的日期格式的字符串。  
  
## <a name="culture-sensitive-functions"></a>区分区域性的函数  
 所有 Visual Basic 字符串转换函数 (除`Str`和`Val`函数) 使用应用程序的区域性信息以确保转换和比较适合于应用程序的区域性用户。  
  
 已成功使用不同的区域性设置的计算机运行的应用程序中使用字符串转换函数的关键是了解哪个函数将使用特定的区域性设置，并使用当前区域性设置。 请注意，应用程序的区域性设置，默认情况下，继承自的操作系统的区域性设置。 有关详细信息，请参阅<xref:Microsoft.VisualBasic.Strings.Asc%2A>， <xref:Microsoft.VisualBasic.Strings.AscW%2A>， <xref:Microsoft.VisualBasic.Strings.Chr%2A>， <xref:Microsoft.VisualBasic.Strings.ChrW%2A>， <xref:Microsoft.VisualBasic.Strings.Format%2A>， <xref:Microsoft.VisualBasic.Conversion.Hex%2A>， <xref:Microsoft.VisualBasic.Conversion.Oct%2A>，并且[类型转换函数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
  
 `Str` （将数字转换为字符串） 和`Val`（将字符串转换为数字） 函数字符串和数字之间进行转换时不使用应用程序的区域性信息。 相反，它们将句点 （.） 识别为有效的小数分隔符。 可识别区域性的这些函数是：  
  
-   **使用当前区域性的转换。** `CStr`并`Format`函数将数字转换为字符串，并`CDbl`和`CInt`函数将字符串转换为数字。  
  
-   **使用特定区域性的转换。** 每个数字的对象都有`ToString(IFormatProvider)`方法，将数字转换为字符串，该方法和一个`Parse(String, IFormatProvider)`方法将字符串转换为数字。 例如，`Double`类型提供了<xref:System.Double.ToString%28System.IFormatProvider%29>和<xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>方法。  
  
 有关详细信息，请参阅 <xref:Microsoft.VisualBasic.Conversion.Str%2A> 和 <xref:Microsoft.VisualBasic.Conversion.Val%2A>。  
  
## <a name="using-a-specific-culture"></a>使用非特定区域性  
 假设您正在开发的应用程序将日期 （格式为字符串） 发送到 Web 服务。 在这种情况下，你的应用程序必须使用特定区域性的字符串转换。 为了说明原因，请考虑使用的日期的结果<xref:System.DateTime.ToString>方法：如果应用程序使用该方法来设置日期 2005 年 7 月 4 日，它将返回"2005 年 7 月 4 日上午 12:00:00"运行时与美国英语 (EN-US) 区域性，但它会返回"04.07.2005 00:00:00"德语 (DE-DE) 区域性与运行时。  
  
 如果您需要执行特定区域性格式的字符串转换，则应使用`CultureInfo`类的内置于[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。 您可以创建一个新`CultureInfo`针对特定区域性的区域性的将名称传递给对象<xref:System.Globalization.CultureInfo.%23ctor%2A>构造函数。 中列出了支持的区域性名称<xref:System.Globalization.CultureInfo>类帮助页。  
  
 或者，可以获取的实例*固定区域性*从<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>属性。 固定区域性基于英语的区域性，但有一些差异。 例如，固定区域性指定而不是采用 12 小时制采用 24 小时制。  
  
 若要将日期转换为区域性的字符串，将传递<xref:System.Globalization.CultureInfo>对象与日期对象<xref:System.DateTime.ToString%28System.IFormatProvider%29>方法。 例如，下面的代码显示"07/04/2005年 00:00:00"，无论应用程序的区域性设置。  
  
 [!code-vb[VbVbalrConcepts#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Date 文本始终解释取决于英语区域性设置。  
  
## <a name="comparing-strings"></a>比较字符串  
 有两个重要的情况下，需要字符串比较：  
  
-   **向用户显示的数据进行排序。** 使用基于当前区域性，因此字符串正确排序的操作。  
  
-   **确定是否两个应用程序内部字符串完全匹配 （通常出于安全目的）。** 使用忽略当前区域性的操作。  
  
 您可以执行这两种类型的比较使用 Visual Basic<xref:Microsoft.VisualBasic.Strings.StrComp%2A>函数。 指定可选`Compare`参数来控制的比较的类型：`Text`大多数输入和输出`Binary`用于确定完全匹配项。  
  
 `StrComp`函数返回一个整数，指示基于排序顺序比较的两个字符串之间的关系。 结果是正数值指示第一个字符串大于第二个字符串。 产生负数结果指示第一个字符串是较小，零指示字符串相等。  
  
 [!code-vb[VbVbalrStrings#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#22)]  
  
 此外可以使用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]合作伙伴`StrComp`函数，<xref:System.String.Compare%2A?displayProperty=nameWithType>方法。 这是基础字符串类的静态，重载方法。 下面的示例演示如何使用此方法：  
  
 [!code-vb[VbVbalrStrings#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#48)]  
  
 更好地控制如何执行比较，可以使用的其他重载<xref:System.String.Compare%2A>方法。 与<xref:System.String.Compare%2A?displayProperty=nameWithType>方法中，可以使用`comparisonType`参数，以指定要使用的比较类型。  
  
|值为`comparisonType`参数|比较类型|何时使用|  
|---|---|---|  
|`Ordinal`|基于字符串的组件字节比较。|比较时使用此值： 区分大小写的标识符、 与安全相关的设置或其他非语言标识符的字节数必须完全匹配。|  
|`OrdinalIgnoreCase`|基于字符串的组件字节比较。<br /><br /> `OrdinalIgnoreCase` 使用固定区域性信息来确定当两个字符的区别只在于大小写。|比较时使用此值： 不区分大小写的标识符、 与安全相关的设置和在 Windows 中存储的数据。|  
|`CurrentCulture` 或 `CurrentCultureIgnoreCase`|比较基于当前区域性中的字符串的解释。|比较时使用这些值： 显示给用户，大多数用户输入，以及需要语言学解读的其他数据的数据。|  
|`InvariantCulture` 或 `InvariantCultureIgnoreCase`|基于字符串的解读中固定区域性的比较。<br /><br /> 这是不同于`Ordinal`和`OrdinalIgnoreCase`，因为固定区域性将其接受范围以外的字符视为等效的固定字符。|仅当比较持久数据或显示的语言相关数据时，需要固定的排序顺序，请使用这些值。|  
  
### <a name="security-considerations"></a>安全注意事项  
 如果你的应用程序做出安全决策基于比较或大小写更改操作的结果，则该操作应使用<xref:System.String.Compare%2A?displayProperty=nameWithType>方法，并传入`Ordinal`或`OrdinalIgnoreCase`为`comparisonType`参数。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Globalization.CultureInfo>
- [Visual Basic 中的字符串简介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [类型转换函数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
