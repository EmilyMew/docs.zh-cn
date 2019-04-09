---
title: 如何：将多个事件连接到 Windows 窗体中的单个事件处理程序
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: d55ccc21efb92ba1e51f4ae88be5025f2f80905b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117957"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>如何：将多个事件连接到 Windows 窗体中的单个事件处理程序
在应用程序设计中，您可能会发现需要使用多个事件的单个事件处理程序或具有多个事件执行相同的过程。 例如，它通常是功能强大的时间-保护程序已引发相同的事件，你的窗体上的按钮一样如果它们公开相同的功能的菜单命令。 您可以执行此操作通过使用属性窗口中的事件视图C#或使用`Handles`关键字和**类名**并**方法名称**下拉列表框在 Visual Basic 代码编辑器中。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>若要将多个事件连接到在 Visual Basic 中的单个事件处理程序  
  
1.  右键单击窗体，然后选择**查看代码**。  
  
2.  从**类名**下拉列表框中，选择一个想要处理的事件处理程序的控件。  
  
3.  从**方法名称**下拉列表框中，选择你想要处理的事件处理程序的事件之一。  
  
4.  在代码编辑器将插入相应的事件处理程序，并将插入点放在方法内。 在下面的示例中，它是<xref:System.Windows.Forms.Control.Click>事件<xref:System.Windows.Forms.Button>控件。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  追加的其他事件所处理到`Handles`子句。  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  将相应的代码添加到事件处理程序。  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>若要将多个事件连接到在 C 中的单个事件处理程序\#
  
1.  选择你想要连接的事件处理程序的控件。  
  
2.  在属性窗口中，单击**事件**按钮 (![事件按钮](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。  
  
3.  单击你想要处理的事件的名称。  
  
4.  在事件名称旁边的值部分中，单击下拉列表按钮以显示与你想要处理的事件的方法签名匹配的现有事件处理程序的列表。  
  
5.  从列表中选择相应的事件处理程序。  
  
     代码将添加到要将事件绑定到现有的事件处理程序的窗体。  
  
## <a name="see-also"></a>请参阅

- [在 Windows 窗体中创建事件处理程序](creating-event-handlers-in-windows-forms.md)
- [事件处理程序概述](event-handlers-overview-windows-forms.md)
