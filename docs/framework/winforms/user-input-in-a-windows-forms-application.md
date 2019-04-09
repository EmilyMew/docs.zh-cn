---
title: Windows 窗体应用程序中的用户输入
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 0eb39f0ecd8fcd12918b38bd77fed2ff32cac1d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124145"
---
# <a name="user-input-in-a-windows-forms-application"></a>Windows 窗体应用程序中的用户输入
在 Windows 窗体中用户输入发送到 Windows 消息的窗体中的应用程序。 一系列可重写方法处理这些消息在应用程序窗体，并控制级别。 这些方法接收鼠标和键盘消息，它们会引发可进行处理以获取信息鼠标或键盘输入的事件。 在许多情况下，Windows 窗体应用程序将能够处理所有用户输入，只需通过处理这些事件。 在其他情况下，应用程序可能需要重写用于处理消息，以便收到通过应用程序、 窗体或控件之前截获特定消息的方法之一。  
  
## <a name="mouse-and-keyboard-events"></a>鼠标和键盘事件  
 所有 Windows 窗体控件都继承一的组与鼠标和键盘输入相关的事件。 例如，控件可以处理<xref:System.Windows.Forms.Control.KeyPress>事件以确定按下的键的字符代码或控件可以处理<xref:System.Windows.Forms.Control.MouseClick>事件以确定鼠标的位置单击。 鼠标和键盘事件的详细信息，请参阅[使用键盘事件](using-keyboard-events.md)并[Windows 窗体中的鼠标事件](mouse-events-in-windows-forms.md)。  
  
## <a name="methods-that-process-user-input-messages"></a>用于处理用户输入的消息的方法  
 窗体和控件有权访问<xref:System.Windows.Forms.IMessageFilter>接口和一组用于处理 Windows 消息的消息队列中的不同点的可重写方法。 这些方法都有<xref:System.Windows.Forms.Message>参数，它封装 Windows 消息的低级别详细信息。 可以实现，也可以重写这些方法以检查的消息，然后使用该消息或将其传递到消息队列中的下一步使用者。 下表列出了用于处理 Windows 窗体中的所有 Windows 消息的方法。  
  
|方法|说明|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|此方法截获排队应用程序级别 （也称为已发布） 的 Windows 消息。|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|此方法截获 Windows 消息在窗体和控件级别之前已处理。|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|此方法处理 Windows 消息级别的窗体和控件。|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|此方法执行级别的窗体和控件的 Windows 消息的默认处理。 这提供了一个窗口的最少功能。|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|处理完后，此方法将截获消息在窗体和控件的级别。 <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage>样式位，必须为要在调用此方法设置。|  
  
 由一组额外的特定于这些类型的消息的可重写方法还处理键盘和鼠标消息。 有关详细信息，请参阅[键盘输入工作原理](how-keyboard-input-works.md)并[鼠标输入工作原理在 Windows 窗体中](how-mouse-input-works-in-windows-forms.md)。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体中的用户输入](user-input-in-windows-forms.md)
- [Windows 窗体应用程序中的键盘输入](keyboard-input-in-a-windows-forms-application.md)
- [Windows 窗体应用程序中的鼠标输入](mouse-input-in-a-windows-forms-application.md)
