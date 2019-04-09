---
title: 如何：使用 Windows 窗体 MonthCalendar 控件以粗体显示特定日期
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- calendars [Windows Forms], displaying dates in bold
- examples [Windows Forms], calendar controls
- GetDayBold event
- MonthCalendar control [Windows Forms], dates displayed in bold
ms.assetid: 8b20db5b-8118-4825-90e8-2c45c186ac7d
ms.openlocfilehash: cf3ec21aa0272f60599f5659d78214120bcfcaf8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073690"
---
# <a name="how-to-display-specific-days-in-bold-with-the-windows-forms-monthcalendar-control"></a>如何：使用 Windows 窗体 MonthCalendar 控件以粗体显示特定日期
Windows 窗体<xref:System.Windows.Forms.MonthCalendar>控件可以显示天以粗体类型为单数形式的日期或重复的基础上。 您可能会这样做可以为特殊日期，例如节假日和周末突出。  
  
 三个属性控制此功能。 <xref:System.Windows.Forms.MonthCalendar.BoldedDates%2A>属性包含一个日期。 <xref:System.Windows.Forms.MonthCalendar.AnnuallyBoldedDates%2A>属性包含显示为粗体每年的日期。 <xref:System.Windows.Forms.MonthCalendar.MonthlyBoldedDates%2A>属性包含以粗体显示每个月的日期。 每个属性包含的数组<xref:System.DateTime>对象。 若要添加或删除其中一个列表中的日期，必须添加或删除<xref:System.DateTime>对象。  
  
### <a name="to-make-a-date-appear-in-bold-type"></a>若要使日期以粗体类型显示  
  
1.  创建<xref:System.DateTime>对象。  
  
    ```vb  
    Dim myVacation1 As Date = New DateTime(2001, 6, 10)  
    Dim myVacation2 As Date = New DateTime(2001, 6, 17)  
    ```  
  
    ```csharp  
    DateTime myVacation1 = new DateTime(2001, 6, 10);  
    DateTime myVacation2 = new DateTime(2001, 6, 17);  
    ```  
  
    ```cpp  
    DateTime myVacation1 = DateTime(2001, 6, 10);  
    DateTime myVacation2 = DateTime(2001, 6, 17);  
    ```  
  
2.  通过调用使单个日期加粗<xref:System.Windows.Forms.MonthCalendar.AddBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.AddAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.AddMonthlyBoldedDate%2A>方法的<xref:System.Windows.Forms.MonthCalendar>控件。  
  
    ```vb  
    MonthCalendar1.AddBoldedDate(myVacation1)  
    MonthCalendar1.AddBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.AddBoldedDate(myVacation1);  
    monthCalendar1.AddBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->AddBoldedDate(myVacation1);  
    monthCalendar1->AddBoldedDate(myVacation2);  
    ```  
  
     - 或 -  
  
     使一组日期以粗体显示一次性创建的数组<xref:System.DateTime>对象并将其分配给其中一个属性。  
  
    ```vb  
    Dim VacationDates As DateTime() = {myVacation1, myVacation2}  
    MonthCalendar1.BoldedDates = VacationDates  
    ```  
  
    ```csharp  
    DateTime[] VacationDates = {myVacation1, myVacation2};  
    monthCalendar1.BoldedDates = VacationDates;  
    ```  
  
    ```cpp  
    Array<DateTime>^ VacationDates = {myVacation1, myVacation2};  
    monthCalendar1->BoldedDates = VacationDates;  
    ```  
  
### <a name="to-make-a-date-appear-in-the-regular-font"></a>若要使日期以常规字体显示  
  
1.  使单个粗体日期以常规字体显示通过调用<xref:System.Windows.Forms.MonthCalendar.RemoveBoldedDate%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAnnuallyBoldedDate%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveMonthlyBoldedDate%2A>方法。  
  
    ```vb  
    MonthCalendar1.RemoveBoldedDate(myVacation1)  
    MonthCalendar1.RemoveBoldedDate(myVacation2)  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveBoldedDate(myVacation1);  
    monthCalendar1.RemoveBoldedDate(myVacation2);  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveBoldedDate(myVacation1);  
    monthCalendar1->RemoveBoldedDate(myVacation2);  
    ```  
  
     - 或 -  
  
     通过调用从一个三个列表中删除所有粗体格式日期<xref:System.Windows.Forms.MonthCalendar.RemoveAllBoldedDates%2A>， <xref:System.Windows.Forms.MonthCalendar.RemoveAllAnnuallyBoldedDates%2A>，或<xref:System.Windows.Forms.MonthCalendar.RemoveAllMonthlyBoldedDates%2A>方法。  
  
    ```vb  
    MonthCalendar1.RemoveAllBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.RemoveAllBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->RemoveAllBoldedDates();  
    ```  
  
2.  通过调用更新的字体的外观<xref:System.Windows.Forms.MonthCalendar.UpdateBoldedDates%2A>方法。  
  
    ```vb  
    MonthCalendar1.UpdateBoldedDates()  
    ```  
  
    ```csharp  
    monthCalendar1.UpdateBoldedDates();  
    ```  
  
    ```cpp  
    monthCalendar1->UpdateBoldedDates();  
    ```  
  
## <a name="see-also"></a>请参阅

- [MonthCalendar 控件](monthcalendar-control-windows-forms.md)
- [如何：在 Windows 窗体 MonthCalendar 控件中选择日期范围](how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)
- [如何：更改 Windows 窗体 MonthCalendar 控件的外观](how-to-change-monthcalendar-control-appearance.md)
- [如何：在 Windows 窗体 MonthCalendar 控件中显示多个月份](display-more-than-one-month-wf-monthcalendar-control.md)
