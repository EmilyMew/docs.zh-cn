---
title: Windows 窗体中的鼠标指针
ms.date: 03/30/2017
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
ms.openlocfilehash: e9b572ba40618a72b8db58917008ebd61a23de79
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122780"
---
# <a name="mouse-pointers-in-windows-forms"></a>Windows 窗体中的鼠标指针
鼠标*指针*，这有时称为游标，是用户输入使用鼠标在屏幕指定的焦点位置的位图。 本主题概述了在 Windows 窗体中鼠标指针，并介绍了一些方法来修改和控制鼠标指针。  
  
## <a name="accessing-the-mouse-pointer"></a>访问鼠标指针  
 表示鼠标指针<xref:System.Windows.Forms.Cursor>类，并且每个<xref:System.Windows.Forms.Control>具有<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>属性，它指定该控件的指针。 <xref:System.Windows.Forms.Cursor>类包含属性的描述指针，如<xref:System.Windows.Forms.Cursor.Position%2A>并<xref:System.Windows.Forms.Cursor.HotSpot%2A>属性和方法可以修改的指针的外观，如<xref:System.Windows.Forms.Cursor.Show%2A>， <xref:System.Windows.Forms.Cursor.Hide%2A>，并<xref:System.Windows.Forms.Cursor.DrawStretched%2A>方法。  
  
## <a name="controlling-the-mouse-pointer"></a>控制鼠标指针  
 有时你可能想要限制的区域的鼠标指针可以使用，或者更改鼠标的位置。 可以获取或设置鼠标使用的当前位置<xref:System.Windows.Forms.Cursor.Position%2A>属性的<xref:System.Windows.Forms.Cursor>。 此外，可以限制可以使用鼠标指针的区域是设置<xref:System.Windows.Forms.Cursor.Clip%2A>属性。 剪辑区域中的，默认情况下是整个屏幕。  
  
## <a name="changing-the-mouse-pointer"></a>更改鼠标指针  
 更改鼠标指针是一种向用户提供反馈的重要方式。 中的处理程序中，例如，可以修改鼠标指针<xref:System.Windows.Forms.Control.MouseEnter>和<xref:System.Windows.Forms.Control.MouseLeave>事件告诉用户发生的计算和限制控件中的用户交互。 有时，鼠标指针将因系统事件，例如当你的应用程序涉及在拖放操作中。  
  
 若要更改鼠标指针的主要方法是通过设置<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.Control.DefaultCursor%2A>到一个新控件的属性<xref:System.Windows.Forms.Cursor>。 有关更改鼠标指针的示例，请参阅中的代码示例<xref:System.Windows.Forms.Cursor>类。 此外，<xref:System.Windows.Forms.Cursors>类公开的一组<xref:System.Windows.Forms.Cursor>许多不同类型的指针，如类似于手的指针的对象。 若要显示等待指针，它类似于一个沙漏，每当在鼠标指针位于控件上时，使用<xref:System.Windows.Forms.Control.UseWaitCursor%2A>属性的<xref:System.Windows.Forms.Control>类。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Cursor>
- [Windows 窗体应用程序中的鼠标输入](mouse-input-in-a-windows-forms-application.md)
- [Windows 窗体中的拖放功能](drag-and-drop-functionality-in-windows-forms.md)
