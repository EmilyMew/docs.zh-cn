---
title: 如何：在 Windows 窗体 MonthCalendar 控件中选择日期范围
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- dates [Windows Forms], selecting range in calendar controls
- examples [Windows Forms], calendar controls
- calendars [Windows Forms], selecting date range
- MonthCalendar control [Windows Forms], selecting date range
ms.assetid: 95d9ab95-b0f8-4c19-9f63-b5cd4593a5d0
ms.openlocfilehash: 0e032a6285c43d7e96c7d59444da6d6598bd8100
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129943"
---
# <a name="how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control"></a>如何：在 Windows 窗体 MonthCalendar 控件中选择日期范围
Windows 窗体的一个重要功能<xref:System.Windows.Forms.MonthCalendar>控件是用户可以选择日期范围内的。 此功能是对的日期选择功能的改进<xref:System.Windows.Forms.DateTimePicker>控件，仅使用户能够选择单个日期/时间值。 可以设置的日期范围或获取由用户设置使用的属性的选择范围<xref:System.Windows.Forms.MonthCalendar>控件。 下面的代码示例演示如何设置选择范围。  
  
### <a name="to-select-a-range-of-dates"></a>若要选择的日期范围  
  
1.  创建<xref:System.DateTime>对象表示范围中的第一个和最后一个日期。  
  
    ```vb  
    Dim projectStart As Date = New DateTime(2001, 2, 13)  
    Dim projectEnd As Date = New DateTime(2001, 2, 28)  
    ```  
  
    ```csharp  
    DateTime projectStart = new DateTime(2001, 2, 13);  
    DateTime projectEnd = new DateTime(2001, 2, 28);  
    ```  
  
    ```cpp  
    DateTime projectStart = DateTime(2001, 2, 13);  
    DateTime projectEnd = DateTime(2001, 2, 28);  
    ```  
  
2.  设置 <xref:System.Windows.Forms.MonthCalendar.SelectionRange%2A> 属性。  
  
    ```vb  
    MonthCalendar1.SelectionRange = New SelectionRange(projectStart, projectEnd)  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionRange = new SelectionRange(projectStart, projectEnd);  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionRange = gcnew  
       SelectionRange(projectStart, projectEnd);  
    ```  
  
     - 或 -  
  
     设置 <xref:System.Windows.Forms.MonthCalendar.SelectionStart%2A> 和 <xref:System.Windows.Forms.MonthCalendar.SelectionEnd%2A> 属性。  
  
    ```vb  
    MonthCalendar1.SelectionStart = projectStart  
    MonthCalendar1.SelectionEnd = projectEnd  
    ```  
  
    ```csharp  
    monthCalendar1.SelectionStart = projectStart;  
    monthCalendar1.SelectionEnd = projectEnd;  
    ```  
  
    ```cpp  
    monthCalendar1->SelectionStart = projectStart;  
    monthCalendar1->SelectionEnd = projectEnd;  
    ```  
  
## <a name="see-also"></a>请参阅

- [MonthCalendar 控件](monthcalendar-control-windows-forms.md)
- [如何：更改 Windows 窗体 MonthCalendar 控件的外观](how-to-change-monthcalendar-control-appearance.md)
- [如何：使用 Windows 窗体 MonthCalendar 控件以粗体显示特定日期](display-specific-days-in-bold-with-wf-monthcalendar-control.md)
- [如何：在 Windows 窗体 MonthCalendar 控件中显示多个月份](display-more-than-one-month-wf-monthcalendar-control.md)
