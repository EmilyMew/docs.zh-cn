---
title: 使用日历
ms.date: 04/01/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET], calendars
- calendars, global applications
- global applications, calendars
- world-ready applications, calendars
- international applications [.NET], calendars
- culture, calendars
ms.assetid: 0c1534e5-979b-4c8a-a588-1c24301aefb3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0113ef84c2b3e42f6d14d25747f7fdbb836a212
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055308"
---
# <a name="working-with-calendars"></a>使用日历

尽管日期和时间值表示时间中的某一刻，但其字符串表示形式区分区域性，并取决于特定区域性显示日期和时间值所用的约定以及该区域性使用的日历。 本主题介绍了.NET 中的日历的支持，并讨论使用日历类，使用日期值时。

## <a name="calendars-in-net"></a>.NET 中的日历

在.NET 中的所有日历都派生<xref:System.Globalization.Calendar?displayProperty=nameWithType>类，该类提供了基本日历实现。 从 <xref:System.Globalization.Calendar> 类继承的类之一是 <xref:System.Globalization.EastAsianLunisolarCalendar> 类，该类是所有阴阳历的基类。 .NET 包括以下日历实现：

* <xref:System.Globalization.ChineseLunisolarCalendar>表示中国阴阳历。

* <xref:System.Globalization.GregorianCalendar>表示公历。 此日历进一步细分为 <xref:System.Globalization.GregorianCalendarTypes?displayProperty=nameWithType> 枚举定义的子类型（如阿拉伯和中东法国）。 <xref:System.Globalization.GregorianCalendar.CalendarType%2A?displayProperty=nameWithType> 属性指定公历的子类型。

* <xref:System.Globalization.HebrewCalendar>表示希伯来历。

* <xref:System.Globalization.HijriCalendar>表示回历。

* <xref:System.Globalization.JapaneseCalendar>表示日本历。

* <xref:System.Globalization.JapaneseLunisolarCalendar>表示日本阴阳历。

* <xref:System.Globalization.JulianCalendar>表示罗马儒略历。

* <xref:System.Globalization.KoreanCalendar>表示朝鲜历。

* <xref:System.Globalization.KoreanLunisolarCalendar>表示朝鲜阴阳历。

* <xref:System.Globalization.PersianCalendar>表示波斯历。

* <xref:System.Globalization.TaiwanCalendar>表示台湾历。

* <xref:System.Globalization.TaiwanLunisolarCalendar>表示台湾阴阳历。

* <xref:System.Globalization.ThaiBuddhistCalendar>表示泰国佛历。

* <xref:System.Globalization.UmAlQuraCalendar>表示古兰经历。

可通过以下两种方法之一来使用日历：

* 作为特定区域性使用的日历。 每个 <xref:System.Globalization.CultureInfo> 对象都有当前日历，这是该对象当前使用的日历。 所有日期和时间值的字符串表示形式会自动反映当前的区域性及其当前日历。 通常，当前的日历是该区域性的默认日历。 <xref:System.Globalization.CultureInfo> 对象还具有可选日历，其中包括该区域性可以使用的其他日历。

* 作为与特定区域性无关的独立日历。 在这种情况下，<xref:System.Globalization.Calendar> 方法用于将日期表示为反映日历的值。

请注意，以下六个日历类只能用作独立日历：<xref:System.Globalization.ChineseLunisolarCalendar>、<xref:System.Globalization.JapaneseLunisolarCalendar>、<xref:System.Globalization.JulianCalendar>、<xref:System.Globalization.KoreanLunisolarCalendar>、<xref:System.Globalization.PersianCalendar> 和 <xref:System.Globalization.TaiwanLunisolarCalendar>。 任何区域性都不将这些日历用作默认日历或可选日历。

## <a name="calendars-and-cultures"></a>日历和区域性

每个区域性都有默认日历，由 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 属性定义。 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 属性可返回 <xref:System.Globalization.Calendar> 对象的数组，该数组指定特定区域性支持的所有日历，包括该区域性的默认日历。

下面的示例演示 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 属性。 该示例为泰语（泰国）和日语（日本）区域性创建 `CultureInfo` 对象，并显示它们的默认和可选日历。 请注意，在这两种情况下，区域性的默认日历也包括在 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 集合中。

[!code-csharp[Conceptual.Calendars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/calendarinfo1.cs#1)]
[!code-vb[Conceptual.Calendars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/calendarinfo1.vb#1)]

特定 <xref:System.Globalization.CultureInfo> 对象当前正在使用的日历由区域性的 <xref:System.Globalization.DateTimeFormatInfo.Calendar%2A?displayProperty=nameWithType> 属性定义。 区域性的 <xref:System.Globalization.DateTimeFormatInfo> 对象由 <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> 属性返回。 创建区域性时，其默认值与 <xref:System.Globalization.CultureInfo.Calendar%2A?displayProperty=nameWithType> 属性的值相同。 但是，可将区域性的当前日历更改为 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 属性返回的数组中包含的任何日历。 如果尝试将当前日历设置为 <xref:System.Globalization.CultureInfo.OptionalCalendars%2A?displayProperty=nameWithType> 属性值中不包括的日历，则会引发 <xref:System.ArgumentException>。

以下示例将更改阿拉伯（沙特阿拉伯）区域性使用的日历。 它首先实例化一个 <xref:System.DateTime> 值并使用当前区域性（在此示例中，为英语（美国））和当前区域性的日历（在此示例中，为公历）显示该值。 接下来，该示例将当前区域性更改为阿拉伯语（沙特阿拉伯），并使用其默认的古兰经历显示该日期。 然后，该示例调用 `CalendarExists` 方法来确定阿拉伯语（沙特阿拉伯）区域性是否支持该回历。 因为该日历受支持，所以该示例将当前日历更改为回历并再次显示日期。 请注意，在每种情况下，均使用当前区域性的当前日历来显示日期。

[!code-csharp[Conceptual.Calendars#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/changecalendar2.cs#2)]
[!code-vb[Conceptual.Calendars#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/changecalendar2.vb#2)]

## <a name="dates-and-calendars"></a>日期和日历

除包括 <xref:System.Globalization.Calendar> 类型参数并允许日期的元素（即月、日和年）以指定日历反映值的构造函数外，<xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值始终基于公历。 例如，这意味着 <xref:System.DateTime.Year%2A?displayProperty=nameWithType> 属性返回公历的年，<xref:System.DateTime.Day%2A?displayProperty=nameWithType> 属性返回公历的当月日期。

> [!IMPORTANT]
> 请记住，日期值与其字符串表示形式之间是有差异的，这一点很重要。 前者基于公历，后者基于特定区域性的当前日历。

下面的示例演示了 <xref:System.DateTime> 属性与其对应的 <xref:System.Globalization.Calendar> 方法之间的这一差异。 在此示例中，当前区域性为阿拉伯语（埃及），当前日历为古兰经历。 <xref:System.DateTime> 值设置为 2011 年 7 月 15 日。 很显然，该值被解释为公历日期，因为这些相同的值是由 <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> 方法在使用不变区域性的约定时返回的。 使用当前区域性的约定设置格式后，该日期的字符串表示形式为 14/08/32，与古兰经历中的日期等效。 接下来，使用 `DateTime` 和 `Calendar` 的成员返回 <xref:System.DateTime> 值的日、月和年。 在每种情况下，<xref:System.DateTime> 成员返回的值反映公历中的值，而 <xref:System.Globalization.UmAlQuraCalendar> 成员返回的值反映古兰经历中的值。

[!code-csharp[Conceptual.Calendars#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/datesandcalendars2.cs#3)]
[!code-vb[Conceptual.Calendars#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/datesandcalendars2.vb#3)]

### <a name="instantiating-dates-based-on-a-calendar"></a>实例化基于日历的日期

由于 <xref:System.DateTime> 和 <xref:System.DateTimeOffset> 值基于公历，因此如果要使用不同日历中的日、月或年的值，必须调用包括 <xref:System.Globalization.Calendar> 类型参数的重载构造函数来实例化日期值。 还可以调用特定日历的 <xref:System.Globalization.Calendar.ToDateTime%2A?displayProperty=nameWithType> 方法的重载之一，以基于特定日历的值来实例化 <xref:System.DateTime> 对象。

下面的示例通过向 <xref:System.DateTime> 构造函数传递一个 <xref:System.Globalization.HebrewCalendar> 对象来实例化一个 <xref:System.DateTime> 值，通过调用 <xref:System.DateTime> 方法来实例化另一个 <xref:System.Globalization.HebrewCalendar.ToDateTime%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Int32%29?displayProperty=nameWithType> 值。 由于这两个值是使用希伯来历中的相同值创建的，因此对 <xref:System.DateTime.Equals%2A?displayProperty=nameWithType> 方法的调用显示这两个 <xref:System.DateTime> 值相等。

[!code-csharp[Conceptual.Calendars#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatehcdate1.cs#4)]
[!code-vb[Conceptual.Calendars#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatehcdate1.vb#4)]

### <a name="representing-dates-in-the-current-calendar"></a>当前日历表示日期

在将日期转换为字符串时，日期和时间格式设置方法始终使用当前日历。 这意味着，年、月和当月日期的字符串表示形式反映当前日历，不一定反映公历。

下面的示例演示当前日历如何影响日期的字符串表示形式。 该示例将当前区域性更改为中文（繁体，台湾），并实例化日期值。 然后，该示例显示当前日历和日期，将当前日历更改为 <xref:System.Globalization.TaiwanCalendar>，并再次显示当前日历和日期。 初次显示日期时，它表示为公历日期。 第二次显示日期时，它表示为台湾日历中的日期。

[!code-csharp[Conceptual.Calendars#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/currentcalendar1.cs#5)]
[!code-vb[Conceptual.Calendars#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/currentcalendar1.vb#5)]

### <a name="representing-dates-in-a-non-current-calendar"></a>非当前日历表示日期

若要使用特定区域性的当前日历之外的日历表示日期，必须调用该 <xref:System.Globalization.Calendar> 对象的方法。 例如，<xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType>、<xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> 方法可将年、月和日转换为反映特定日历的值。

> [!WARNING]
> 由于某些日历不是任何区域性的可选日历，因此用这些日历表示日期始终需要调用日历方法。 对于派生自 <xref:System.Globalization.EastAsianLunisolarCalendar>、<xref:System.Globalization.JulianCalendar> 和 <xref:System.Globalization.PersianCalendar> 类的所有日历而言，均为这种情况。

下面的示例使用 <xref:System.Globalization.JulianCalendar> 对象实例化罗马儒略历的日期 1905 年 1 月 9 日。 使用默认（公历）日历显示此日期时，该日期表示为 1905 年 1 月 22 日。 通过调用各种 <xref:System.Globalization.JulianCalendar> 方法，可用罗马儒略历表示日期。

[!code-csharp[Conceptual.Calendars#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/noncurrentcalendar1.cs#6)]
[!code-vb[Conceptual.Calendars#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/noncurrentcalendar1.vb#6)]

### <a name="calendars-and-date-ranges"></a>日历和日期范围

日历支持的最早日期由其 <xref:System.Globalization.Calendar.MinSupportedDateTime%2A?displayProperty=nameWithType> 属性指示。 对于 <xref:System.Globalization.GregorianCalendar> 类，该日期为公历公元 0001 年 1 月 1 日。 大部分.NET 中的其他日历支持更高版本的日期。 尝试使用日历支持的最早日期前面的日期和时间值将引发 <xref:System.ArgumentOutOfRangeException> 异常。

但是，有一个很重要的异常。 <xref:System.DateTime> 对象和 <xref:System.DateTimeOffset> 对象的默认（未初始化的）值等于 <xref:System.Globalization.GregorianCalendar.MinSupportedDateTime%2A?displayProperty=nameWithType> 值。 如果您尝试设置不支持公历公元 0001 年 1 月 1 日的日历中此日期格式 并不提供格式说明符，格式设置方法使用"s"（可排序日期/时间模式） 格式说明符而不是"G"（常规日期/时间模式） 格式说明符。 因此，格式设置操作将不会引发 <xref:System.ArgumentOutOfRangeException> 异常。 相反，它会返回不受支持的日期。 下面的示例阐释了这一点，在使用日语日历将当前区域性设置为日语（日本）以及使用古兰经历将当前区域性设置为阿拉伯语（埃及）时，它将显示 <xref:System.DateTime.MinValue?displayProperty=nameWithType> 的值。 它还会将当前区域性设置为英语（美国），并调用 <xref:System.DateTime.ToString%28System.IFormatProvider%29?displayProperty=nameWithType> 方法以及所有这些 <xref:System.Globalization.CultureInfo> 对象。 在每种情况下，均使用可排序的日期/时间模式来显示日期。

[!code-csharp[Conceptual.Calendars#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/minsupporteddatetime1.cs#11)]
[!code-vb[Conceptual.Calendars#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/minsupporteddatetime1.vb#11)]

## <a name="working-with-eras"></a>使用纪元

日历通常将日期划分为纪元。 但是，<xref:System.Globalization.Calendar>类在.NET 中的不支持由大部分以及日历，定义每个纪元<xref:System.Globalization.Calendar>类支持单个纪元。 只有 <xref:System.Globalization.JapaneseCalendar> 和 <xref:System.Globalization.JapaneseLunisolarCalendar> 类支持多个纪元。

> [!IMPORTANT]
>  Reiwa 时代、 新纪元<xref:System.Globalization.JapaneseCalendar>和<xref:System.Globalization.JapaneseLunisolarCalendar>，2019 年 5 月 1 日，将从开始。 此更改会影响使用这些日历的所有应用程序。 请参阅以下文章，了解详细信息：
> - [处理在.NET 中的日语日历中的新时代](https://devblogs.microsoft.com/dotnet/handling-a-new-era-in-the-japanese-calendar-in-net/)，记录添加到.NET 可支持的功能与多个纪元的日历和讨论多纪元的日历处理时要使用的最佳实践。
> - [准备用于日语纪元更改应用程序](/windows/uwp/design/globalizing/japanese-era-change)，其中提供有关测试 Windows 上的应用程序，以确保其变更就绪的纪元的信息。
> - [新的日语时代的摘要更新为.NET Framework](https://support.microsoft.com/en-us/help/4477957/new-japanese-era-updates-for-net-framework)，其中列出了与新的日语日历时代，相关的各个 Windows 版本的.NET Framework 更新说明新的.NET Framework 功能，有关多纪元支持，并包括若要在测试应用程序中查找的内容。

大多数日历中的某个时间段表示相当长的时间段。 例如，在公历日历中，当前纪元跨越多个两个很长时间以来。 有关<xref:System.Globalization.JapaneseCalendar>和<xref:System.Globalization.JapaneseLunisolarCalendar>，两个日历支持的多个纪元，这不是这种情况。 某个时间段对应于皇帝的残暴的段。 支持多个纪元，尤其是在当前纪元的上限值未知时, 带来了特殊的挑战。 

### <a name="eras-and-era-names"></a>纪元和纪元名称

在.NET 中，表示特定日历实现支持的纪元的整数存储按相反的顺序在<xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType>数组。 当前纪元 （这是最新时间范围内的纪元） 是在索引为零，且针对<xref:System.Globalization.Calendar>类支持多个纪元，每个后续索引反映前一个纪元。 静态的 <xref:System.Globalization.Calendar.CurrentEra?displayProperty=nameWithType> 属性定义当前纪元在 <xref:System.Globalization.Calendar.Eras%2A?displayProperty=nameWithType> 数组中的索引；它是一个值始终为零的常数。 各个 <xref:System.Globalization.Calendar> 类还包括可返回当前纪元值的静态字段。 下表中列出了这些字段。

| 日历类                                        | 当前纪元字段                                                 |
| ----------------------------------------------------- | ----------------------------------------------------------------- |
| <xref:System.Globalization.ChineseLunisolarCalendar>  | <xref:System.Globalization.ChineseLunisolarCalendar.ChineseEra>   |
| <xref:System.Globalization.GregorianCalendar>         | <xref:System.Globalization.GregorianCalendar.ADEra>               |
| <xref:System.Globalization.HebrewCalendar>            | <xref:System.Globalization.HebrewCalendar.HebrewEra>              |
| <xref:System.Globalization.HijriCalendar>             | <xref:System.Globalization.HijriCalendar.HijriEra>                |
| <xref:System.Globalization.JapaneseLunisolarCalendar> | <xref:System.Globalization.JapaneseLunisolarCalendar.JapaneseEra> |
| <xref:System.Globalization.JulianCalendar>            | <xref:System.Globalization.JulianCalendar.JulianEra>              |
| <xref:System.Globalization.KoreanCalendar>            | <xref:System.Globalization.KoreanCalendar.KoreanEra>              |
| <xref:System.Globalization.KoreanLunisolarCalendar>   | <xref:System.Globalization.KoreanLunisolarCalendar.GregorianEra>  |
| <xref:System.Globalization.PersianCalendar>           | <xref:System.Globalization.PersianCalendar.PersianEra>            |
| <xref:System.Globalization.ThaiBuddhistCalendar>      | <xref:System.Globalization.ThaiBuddhistCalendar.ThaiBuddhistEra>  |
| <xref:System.Globalization.UmAlQuraCalendar>          | <xref:System.Globalization.UmAlQuraCalendar.UmAlQuraEra>          |

通过将特定纪元编号传递给 <xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType> 或 <xref:System.Globalization.DateTimeFormatInfo.GetAbbreviatedEraName%2A?displayProperty=nameWithType> 方法，可检索与该纪元编号对应的名称。 下面的示例调用这些方法来检索有关 <xref:System.Globalization.GregorianCalendar> 类中的纪元支持信息。 它将显示对应于当前纪元的第二年的 1 月 1 日的公历日期，以及对应的每个受支持的日本历时代的第二 1 年月 1 日的公历日期。

[!code-csharp[Conceptual.Calendars#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/instantiatewithera1.cs)]
[!code-vb[Conceptual.Calendars#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/instantiatewithera1.vb)]

此外，“g”自定义日期和时间格式字符串还包括一个日期和时间的字符串表示形式的日期纪元名称。 有关详细信息，请参阅[自定义日期和时间格式字符串](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)。

### <a name="instantiating-a-date-with-an-era"></a>实例化用纪元日期

为两个<xref:System.Globalization.Calendar>支持多个纪元的类，由特定年、 月和天的月份值组成的日期可能不明确。 例如，所有支持的纪元<xref:System.Globalization.JapaneseCalendar>具有其编号为 1 年。 通常，如果未指定纪元，则日期和时间以及日历方法都假定该值属于当前纪元。 这是的则返回 true<xref:System.DateTime.%23ctor%2A>并<xref:System.DateTimeOffset.%23ctor%2A>包含的类型参数的构造函数<xref:System.Globalization.Calendar>，并将[JapaneseCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32))和[JapaneseLunisolarCalendar.ToDateTime](xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32))方法。 下面的示例实例化表示第二个的未指定纪元年份的 1 月 1 日的日期。 如果您执行该示例时 Reiwa 纪元是当前纪元，日期被解释为 Reiwa 时代的第二年。 时代，令和，年份中返回的字符串之前<xref:System.DateTime.ToString(System.String,System.IFormatProvider)?displayProperty=nameWithType>方法和对应于 2020 年 1 月 1 日，公历日历中。 （Reiwa 纪元在公历日历以来的 2019 年开始。）

[!code-csharp[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/cs/program.cs)]
[!code-vb[A date in the current era](~/samples/snippets/standard/datetime/calendars/current-era/vb/program.vb)]

但是，如果时代发生更改，则此代码的意图变得不明确。 日期用于表示当前纪元的第二年或旨在表示平成纪元的第二个年份？ 有两种方法来避免这种歧义：

- 实例化使用默认的日期和时间值<xref:System.Globalization.GregorianCalendar>类。 然后可以使用日语日历或日语阴阳历的日期，如以下示例所示的字符串表示形式。

   [!code-csharp[Insantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/cs/program.cs)]
   [!code-vb[Instantiating a Gregorian date](~/samples/snippets/standard/datetime/calendars/gregorian/vb/program.vb)]

- 调用显式指定纪元的日期和时间的方法。 这包括以下方法：

   - <xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)>方法<xref:System.Globalization.JapaneseCalendar>或<xref:System.Globalization.JapaneseLunisolarCalendar>类。

   - 一个<xref:System.DateTime>或<xref:System.DateTimeOffset>分析方法，例如<xref:System.DateTime.Parse%2A>， <xref:System.DateTime.TryParse%2A>， <xref:System.DateTime.ParseExact%2A>，或<xref:System.DateTime.TryParseExact%2A>，其中包括要分析的字符串和 （可选）<xref:System.Globalization.DateTimeStyles>参数，如果当前区域性为日语日语 ("JA-JP") 和该区域性的日历是<xref:System.Globalization.JapaneseCalendar>。 要分析的字符串必须包括纪元。

   - 一个<xref:System.DateTime>或<xref:System.DateTimeOffset>分析包括方法`provider`类型的参数<xref:System.IFormatProvider>。 `provider` 必须是<xref:System.Globalization.CultureInfo>对象，表示其当前日历是日语日本 ("JA-JP") 区域性<xref:System.Globalization.JapaneseCalendar>或<xref:System.Globalization.DateTimeFormatInfo>对象，其<xref:System.Globalization.DateTimeFormatInfo.Calendar>属性是<xref:System.Globalization.JapaneseCalendar>。 要分析的字符串必须包括纪元。

   以下示例使用三个这些方法来实例化的日期和时间明治纪元上 1868 年 9 月 8 日，, 开始和结束 1912 年 7 月 29 日。 

   [!code-csharp[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/cs/program.cs)]
   [!code-vb[A date in a specified era](~/samples/snippets/standard/datetime/calendars/specify-era/vb/program.vb)]

> [!TIP]
> 当使用支持多个纪元的日历*始终*使用公历日期来实例化日期，或指定的纪元的日期和时间基于该日历时实例化。

在指定到某个时间段<xref:System.Globalization.Calendar.ToDateTime(System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32,System.Int32)>方法中，你提供的日历中的纪元的索引<xref:System.Globalization.Calendar.Eras>属性。 对于其纪元可能会有所更改的日历，但是，这些索引不是常量值;当前纪元位于索引 0，并且最早的纪元位于索引`Eras.Length - 1`。 一个新时代添加到日历，以前的纪元的索引加一。 您可以按如下所示提供相应的纪元索引：

- 有关当前纪元中的日期，始终使用日历的<xref:System.Globalization.Calendar.CurrentEra>属性。

- 指定纪元中的日期，使用<xref:System.Globalization.DateTimeFormatInfo.GetEraName%2A?displayProperty=nameWithType>方法来检索与指定的纪元名称相对应的索引。 这就要求<xref:System.Globalization.JapaneseCalendar>进行的当前日历<xref:System.Globalization.CultureInfo>表示 JA-JP 区域性的对象。  (这种技术适合<xref:System.Globalization.JapaneseLunisolarCalendar>，因为它支持作为相同的纪元<xref:System.Globalization.JapaneseCalendar>。)前面的示例演示了此方法。

### <a name="calendars-eras-and-date-ranges-relaxed-range-checks"></a>日历、 纪元和日期范围：宽松的范围检查

很像单个日历具有支持的日期范围中的纪元<xref:System.Globalization.JapaneseCalendar>和<xref:System.Globalization.JapaneseLunisolarCalendar>类还具有受支持的范围。 以前，.NET 使用严格范围进行检查以确保特定于纪元的日期是那个时代的范围内的纪元。 也就是说，如果日期范围内指定纪元，则该方法将引发<xref:System.ArgumentOutOfRangeException>。 目前，.NET 使用默认情况下的宽松范围检查。 更新到所有版本的.NET 都引入宽松的纪元范围检查;尝试实例化指定纪元的范围之外的特定于纪元的日期"溢出"到以下的时代，并不会引发异常。

以下示例尝试实例化 Showa 纪元上 1926 年 12 月 25 日，, 开始和结束 1989 年 1 月 7 日 65th 年的日期。 此日期对应于 1990 年 1 月 9 日，即 Showa 纪元中的范围之外<xref:System.Globalization.JapaneseCalendar>。 如示例输出所示，该示例显示的日期是 1990 年 1 月 9 日，第二个的平成纪元年份中。

   [!code-csharp[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/cs/program.cs)]
   [!code-vb[Relaxed range checks](~/samples/snippets/standard/datetime/calendars/relaxed-range/vb/program.vb)]

如果宽松的范围检查是不可取，则可以还原中通过多种方式，具体取决于你的应用程序正在其运行的.NET 版本的严格范围检查：

- **.NET core:** 可以添加以下 *。 netcore.runtime.json*配置文件：

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.EnforceJapaneseEraYearRanges": true
      } 
   }
   ```

- **.NET framework 4.6 或更高版本：** 您可以设置以下 AppContext 开关：

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceJapaneseEraYearRanges=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 或更早版本：** 您可以设置以下注册表值：

   |  |  |
   |--|--|
   |键 | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |名称 | Switch.System.Globalization.EnforceJapaneseEraYearRanges |
   |类型 | REG_SZ |
   |值 | 1 |

启用严格范围检查，与前面的示例将引发<xref:System.ArgumentOutOfRangeException>并显示以下输出：

```console
Unhandled Exception: System.ArgumentOutOfRangeException: Valid values are between 1 and 64, inclusive.
Parameter name: year
   at System.Globalization.GregorianCalendarHelper.GetYearOffset(Int32 year, Int32 era, Boolean throwOnError)
   at System.Globalization.GregorianCalendarHelper.ToDateTime(Int32 year, Int32 month, Int32 day, Int32 hour, Int32 minute, Int32 second, Int32 millisecond, Int32 era)
   at Example.Main()
```

### <a name="representing-dates-in-calendars-with-multiple-eras"></a>表示具有多个纪元的日历中的日期

如果 <xref:System.Globalization.Calendar> 对象支持纪元并且是 <xref:System.Globalization.CultureInfo> 对象的当前日历，则纪元将包括在完整日期和时间、长日期和短日期模式的日期和时间值的字符串表示形式中。 下面的示例显示当前区域性为日语（日本）并且当前日历为日本日历时的这些日期模式。

[!code-csharp[Conceptual.Calendars#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings1.cs#8)]
[!code-vb[Conceptual.Calendars#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings1.vb#8)]

> [!WARNING]
> <xref:System.Globalization.JapaneseCalendar>类是在多个纪元，并且这两个支持日期可以使用的当前日历的.NET 中的唯一日历类<xref:System.Globalization.CultureInfo>对象-具体而言的<xref:System.Globalization.CultureInfo>表示日语 （日本） 区域性的对象。

对于所有日历，“g”自定义格式说明符会在结果字符串中包括纪元。 下面的示例使用“MM-dd-yyyy g”自定义格式字符串，在当前日历为公历时在结果字符串中包括纪元。

[!code-csharp[Conceptual.Calendars#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings2.cs#9)]
[!code-vb[Conceptual.Calendars#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings2.vb#9)]

当日期的字符串表示形式用非当前日历来表示时，<xref:System.Globalization.Calendar> 类包括一个可与 <xref:System.Globalization.Calendar.GetEra%2A?displayProperty=nameWithType>、<xref:System.Globalization.Calendar.GetYear%2A?displayProperty=nameWithType> 和 <xref:System.Globalization.Calendar.GetMonth%2A?displayProperty=nameWithType> 方法一起使用的 <xref:System.Globalization.Calendar.GetDayOfMonth%2A?displayProperty=nameWithType> 方法，以明确指示日期及其所属纪元。 下面的示例使用 <xref:System.Globalization.JapaneseLunisolarCalendar> 类来提供演示。 但请注意，在结果字符串中包括有意义的名称或缩写（而不是表示纪元的整数）需要您实例化 <xref:System.Globalization.DateTimeFormatInfo> 对象并使 <xref:System.Globalization.JapaneseCalendar> 成为其当前日历。 （<xref:System.Globalization.JapaneseLunisolarCalendar> 日历不能为任何区域性的当前日历，但在此示例中，两个日历共享相同的纪元。）

[!code-csharp[Conceptual.Calendars#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.calendars/cs/formatstrings3.cs#10)]
[!code-vb[Conceptual.Calendars#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.calendars/vb/formatstrings3.vb#10)]

日语日历，在某个时间段的第一年被称为元年 （元年）。 例如，而不是日本平成 12 1 平成时代的第一年可以描述为平成元年。 .NET 采用此约定在格式设置操作的日期和时间与以下标准或自定义日期和时间格式字符串格式一起使用时<xref:System.Globalization.CultureInfo>表示具有的日语日本("JA-JP")区域性的对象<xref:System.Globalization.JapaneseCalendar>类：

- [长日期模式](../base-types/standard-date-and-time-format-strings.md#LongDate)，由"D"标准日期和时间格式字符串。
- [完整日期长时间模式](../base-types/standard-date-and-time-format-strings.md#FullDateLongTime)，由"F"标准日期和时间格式字符串。
- [完整日期短时间模式](../base-types/standard-date-and-time-format-strings.md#FullDateShortTime)，由"f"标准日期和时间格式字符串。
- [年/月模式](../base-types/standard-date-and-time-format-strings.md#YearMonth)，由 Y"或"y"标准日期和时间格式字符串。
- ["Ggy 年"或"ggy年"[自定义日期和时间格式字符串](../base-types/custom-date-and-time-format-strings.md)。

例如，下面的示例显示第一年中的平成纪元的日期<xref:System.Globalization.JapaneseCalendar>。

   [!code-csharp[gannen](~/samples/snippets/standard/datetime/calendars/gannen/cs/program.cs)]
   [!code-vb[gannen](~/samples/snippets/standard/datetime/calendars/gannen/vb/gannen-fmt.vb)]

如果在格式设置操作不需要此行为，可以还原以前的行为，而不是"元年"始终表示为"1"的某个时间段的第一年，通过执行以下操作，具体取决于.NET 的版本：

- **.NET core:** 可以添加以下 *。 netcore.runtime.json*配置文件：

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.FormatJapaneseFirstYearAsANumber": true
      } 
   }
   ```

- **.NET framework 4.6 或更高版本：** 您可以设置以下 AppContext 开关：

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.FormatJapaneseFirstYearAsANumber=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 或更早版本：** 您可以设置以下注册表值：

   |  |  |
   |--|--|
   |键 | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |名称 | Switch.System.Globalization.FormatJapaneseFirstYearAsANumber |
   |类型 | REG_SZ |
   |值 | 1 |

在格式设置操作禁用元年支持，与上面的示例显示以下输出：

```console
Japanese calendar date: 平成1年8月18日 (Gregorian: Friday, August 18, 1989)
```

.NET 也已更新，使日期和时间分析操作中支持包含表示为"1"或元年年份的字符串。 尽管不需要执行此操作，可以还原以前的行为来将只有"1"识别为某个时间段的第一年。 如下所示，具体取决于.NET 的版本，你可以执行此操作：

- **.NET core:** 可以添加以下 *。 netcore.runtime.json*配置文件：

   ```json
   "runtimeOptions": {
      "configProperties": {
         "Switch.System.Globalization.EnforceLegacyJapaneseDateParsing": true
      } 
   }
   ```

- **.NET framework 4.6 或更高版本：** 您可以设置以下 AppContext 开关：

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <configuration>
     <runtime>
       <AppContextSwitchOverrides value="Switch.System.Globalization.EnforceLegacyJapaneseDateParsing=true" />
     </runtime>
   </configuration>
   ```

- **.NET framework 4.5.2 或更早版本：** 您可以设置以下注册表值：

   |  |  |
   |--|--|  
   |键 | HKEY_LOCAL_MACHINE\Software\Microsoft.NETFramework\AppContext |
   |名称 | Switch.System.Globalization.EnforceLegacyJapaneseDateParsing |
   |类型 | REG_SZ |
   |值 | 1 | 

## <a name="see-also"></a>请参阅

- [如何：用非公历日历显示日期](../../../docs/standard/base-types/how-to-display-dates-in-non-gregorian-calendars.md)
- [示例:日历周范围实用工具](https://code.msdn.microsoft.com/NET-Framework-4-Calendar-3360a84a)
- [日历类](xref:System.Globalization.Calendar)
