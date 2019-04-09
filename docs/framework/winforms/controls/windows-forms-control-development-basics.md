---
title: Windows 窗体控件开发基础知识
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: 21b8b08e56e8b4d48fb738b86247d3f04dc4150b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086437"
---
# <a name="windows-forms-control-development-basics"></a>Windows 窗体控件开发基础知识
Windows 窗体控件是派生的类直接或间接从<xref:System.Windows.Forms.Control?displayProperty=nameWithType>。 以下列表描述用于开发 Windows 窗体控件的常见方案：  
  
-   组合现有控件来创作复合控件。  
  
     复合控件封装为控件可以重复使用的用户界面。 复合控件的一个示例是包含一个文本框和重置按钮控件。 可视化设计器提供了用于创建复合控件的丰富支持。 若要创作复合控件，派生<xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>。 类的基类<xref:System.Windows.Forms.UserControl>提供了键盘路由子控件，并使子控件作为组进行处理。 有关详细信息，请参阅[开发复合 Windows 窗体控件](developing-a-composite-windows-forms-control.md)。  
  
-   扩展现有控件进行自定义，或将添加到其功能。  
  
     不能更改其颜色的按钮和一个按钮，跟踪已点击的次数的其他属性是扩展控件的示例。 通过从其派生和重写或添加属性、 方法和事件，可以自定义任何 Windows 窗体控件。  
  
-   创作的控件，不会合并或扩展现有的控件。  
  
     在此方案中，从基类派生你的控件<xref:System.Windows.Forms.Control>。 您可以添加以及重写属性、 方法和事件的基类。 若要开始，请参阅[如何：开发的简单 Windows 窗体控件](how-to-develop-a-simple-windows-forms-control.md)。  
  
 Windows 窗体控件的基类<xref:System.Windows.Forms.Control>，提供所需的客户端的基于 Windows 的应用程序的可视显示的基本功能。 <xref:System.Windows.Forms.Control> 提供窗口句柄、 处理消息路由，并提供鼠标和键盘事件，以及许多其他用户界面事件。 它提供高级的布局，并有特定于可视显示的属性，如<xref:System.Windows.Forms.Control.ForeColor%2A>， <xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.Height%2A>， <xref:System.Windows.Forms.Control.Width%2A>，以及许多其他。 此外，它提供安全性，线程处理支持和 ActiveX 控件与互操作性。 由于基类提供了大量基础结构，因此使开发自己的 Windows 窗体控件变得相对简单。  
  
## <a name="see-also"></a>请参阅

- [如何：开发简单的 Windows 窗体控件](how-to-develop-a-simple-windows-forms-control.md)
- [开发复合 Windows 窗体控件](developing-a-composite-windows-forms-control.md)
- [如何：创建显示进度的 Windows 窗体控件](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [各种自定义控件](varieties-of-custom-controls.md)
