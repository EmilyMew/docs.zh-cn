---
title: Calendar
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: 9a64c6cd6fc1cc53383f2617f7a7a78959e87c4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124781"
---
# <a name="calendar"></a>Calendar
日历，用户选择使用的 visual 日历显示日期。  
  
 一个<xref:System.Windows.Controls.Calendar>自身、 或下拉列表的一部分，可以使用控件<xref:System.Windows.Controls.DatePicker>控件。 有关详细信息，请参阅 <xref:System.Windows.Controls.DatePicker>。  
  
 下图显示了两个<xref:System.Windows.Controls.Calendar>控制，一个选择和中断日期，而无需另一个。  
  
 ![月历控件](./media/ndp-calendarcontrols.png "NDP_CalendarControls")  
日历控件  
  
 下表提供了通常与相关联的任务的信息<xref:System.Windows.Controls.Calendar>。  
  
|任务|实现|  
|----------|--------------------|  
|指定日期不能选择。|使用 <xref:System.Windows.Controls.Calendar.BlackoutDates%2A> 属性。|  
|具有<xref:System.Windows.Controls.Calendar>显示每个月、 整整一年或十年。|设置<xref:System.Windows.Controls.Calendar.DisplayMode%2A>属性设置为月、 年或十年。|  
|指定用户是否可以选择一个日期、 一系列日期或多个范围的日期。|使用<xref:System.Windows.Controls.Calendar.SelectionMode%2A>。|  
|指定的日期范围的<xref:System.Windows.Controls.Calendar>显示。|使用<xref:System.Windows.Controls.Calendar.DisplayDateStart%2A>和<xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A>属性。|  
|指定是否突出显示当前日期。|使用 <xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> 属性。 默认情况下<xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A>是`true`。|  
|更改的大小<xref:System.Windows.Controls.Calendar>。|使用<xref:System.Windows.Controls.Viewbox>，或者设置<xref:System.Windows.FrameworkElement.LayoutTransform%2A>属性设置为<xref:System.Windows.Media.ScaleTransform>。 请注意，如果您设置<xref:System.Windows.FrameworkElement.Width%2A>并<xref:System.Windows.FrameworkElement.Height%2A>的属性<xref:System.Windows.Controls.Calendar>，实际的日历不会更改其大小。|  
  
 <xref:System.Windows.Controls.Calendar>控件提供了使用鼠标或键盘的基本导航。 下表总结了键盘导航。  
  
|组合键|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|操作|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|箭头|<xref:System.Windows.Controls.CalendarMode.Month>|更改<xref:System.Windows.Controls.Calendar.SelectedDate%2A>属性如果<xref:System.Windows.Controls.Calendar.SelectionMode%2A>属性未设置为<xref:System.Windows.Controls.CalendarSelectionMode.None>。|  
|箭头|<xref:System.Windows.Controls.CalendarMode.Year>|更改的月份<xref:System.Windows.Controls.Calendar.DisplayDate%2A>属性。 请注意，<xref:System.Windows.Controls.Calendar.SelectedDate%2A>不会更改。|  
|箭头|<xref:System.Windows.Controls.CalendarMode.Decade>|更改的年份<xref:System.Windows.Controls.Calendar.DisplayDate%2A>。 请注意，<xref:System.Windows.Controls.Calendar.SelectedDate%2A>不会更改。|  
|SHIFT + 箭头|<xref:System.Windows.Controls.CalendarMode.Month>|如果<xref:System.Windows.Controls.Calendar.SelectionMode%2A>未设置为<xref:System.Windows.Controls.CalendarSelectionMode.SingleDate>或<xref:System.Windows.Controls.CalendarSelectionMode.None>，扩展了所选日期范围。|  
|Home|<xref:System.Windows.Controls.CalendarMode.Month>|更改<xref:System.Windows.Controls.Calendar.SelectedDate%2A>到当前月份的第一天。|  
|Home|<xref:System.Windows.Controls.CalendarMode.Year>|更改的月份<xref:System.Windows.Controls.Calendar.DisplayDate%2A>到一年的第一个月。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A>不会更改。|  
|Home|<xref:System.Windows.Controls.CalendarMode.Decade>|更改的年份<xref:System.Windows.Controls.Calendar.DisplayDate%2A>十年的第一年。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A>不会更改。|  
|End|<xref:System.Windows.Controls.CalendarMode.Month>|更改<xref:System.Windows.Controls.Calendar.SelectedDate%2A>到当前月份的最后一天。|  
|End|<xref:System.Windows.Controls.CalendarMode.Year>|更改的月份<xref:System.Windows.Controls.Calendar.DisplayDate%2A>年份的最后一个月。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A>不会更改。|  
|End|<xref:System.Windows.Controls.CalendarMode.Decade>|更改的年份<xref:System.Windows.Controls.Calendar.DisplayDate%2A>十年的最后一年。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A>不会更改。|  
|Ctrl+向上键|任意|切换到下一个更大<xref:System.Windows.Controls.Calendar.DisplayMode%2A>。 如果<xref:System.Windows.Controls.Calendar.DisplayMode%2A>已经是<xref:System.Windows.Controls.CalendarMode.Decade>，执行任何操作。|  
|Ctrl+向下键|任意|切换到下一个较小<xref:System.Windows.Controls.Calendar.DisplayMode%2A>。 如果<xref:System.Windows.Controls.Calendar.DisplayMode%2A>已经是<xref:System.Windows.Controls.CalendarMode.Month>，执行任何操作。|  
|空格键或 ENTER|<xref:System.Windows.Controls.CalendarMode.Year> 或 <xref:System.Windows.Controls.CalendarMode.Decade>|开关<xref:System.Windows.Controls.Calendar.DisplayMode%2A>到<xref:System.Windows.Controls.CalendarMode.Month>或<xref:System.Windows.Controls.CalendarMode.Year>由已设定焦点的项表示。|  
  
## <a name="see-also"></a>请参阅

- [Controls](index.md)
- [样式设置和模板化](styling-and-templating.md)
