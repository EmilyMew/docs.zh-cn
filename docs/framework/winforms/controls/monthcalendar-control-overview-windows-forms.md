---
title: MonthCalendar 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- MonthCalendar
helpviewer_keywords:
- calendars [Windows Forms], Windows Forms controls
- calendar controls [Windows Forms], Windows Forms
- MonthCalendar control [Windows Forms], setting the first day of the week
ms.assetid: 788c5325-b721-44ec-95bf-9b680ba0f6a2
ms.openlocfilehash: 8928a78735392920d893661c70554bd35eba2886
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106231"
---
# <a name="monthcalendar-control-overview-windows-forms"></a>MonthCalendar 控件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.MonthCalendar>控件提供了直观的图形界面的用户可以查看和设置日期信息。 该控件显示一个日历： 包含数月，排列在列下方星期几，与所选的突出显示的日期范围内的网格。 可以通过单击箭头按钮在月标题的任何一侧选择不同的月份。 与类似<xref:System.Windows.Forms.DateTimePicker>控件，您可以选择与此控件的多个日期。 有关详细信息<xref:System.Windows.Forms.DateTimePicker>控件，请参阅[DateTimePicker 控件](datetimepicker-control-windows-forms.md)。  
  
## <a name="configuring-the-monthcalendar-control"></a>配置 MonthCalendar 控件  
 <xref:System.Windows.Forms.MonthCalendar>控件的外观是高度可配置。 默认情况下，今天的日期显示为圆形，并且还显示在网格的底部。 您可以通过设置更改此功能<xref:System.Windows.Forms.MonthCalendar.ShowToday%2A>并<xref:System.Windows.Forms.MonthCalendar.ShowTodayCircle%2A>属性设置为`false`。 您还可以将周数通过设置添加到日历<xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A>属性设置为`true`。 通过设置<xref:System.Windows.Forms.MonthCalendar.CalendarDimensions%2A>属性，可以有多个显示月份水平和垂直方向。 默认情况下，星期日显示为一周的第一天，但可以使用指定的任意日期<xref:System.Windows.Forms.MonthCalendar.FirstDayOfWeek%2A>属性。  
  
 您还可以设置要在中显示的特定日期上一次性，每年或每月，以粗体显示通过添加<xref:System.DateTime>对象添加到<xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>，和<xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>属性。 有关详细信息，请参阅[如何：特定以粗体的显示日期与 Windows 窗体 MonthCalendar 控件](display-specific-days-in-bold-with-wf-monthcalendar-control.md)。  
  
 键属性<xref:System.Windows.Forms.MonthCalendar>控件是<xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>，日期控件中选定的范围。 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A>值不能超过可选择，在中设置最大天数<xref:System.Windows.Forms.MonthCalendar.MaxSelectionCount%2A>属性。 用户可以选择的最早和最新日期由<xref:System.Windows.Forms.MonthCalendar.MaxDate%2A>和<xref:System.Windows.Forms.MonthCalendar.MinDate%2A>属性。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.MonthCalendar>
- [MonthCalendar 控件](monthcalendar-control-windows-forms.md)
