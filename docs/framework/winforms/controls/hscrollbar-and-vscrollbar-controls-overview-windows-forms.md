---
title: HScrollBar 控件和 VScrollBar 控件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- HScrollBar
- VScrollBar
helpviewer_keywords:
- ScrollBar control [Windows Forms]
- HScrollBar control [Windows Forms], about HScrollBar
- VScrollBar control [Windows Forms], about VScrollBar control
- ScrollBar control [Windows Forms], about ScrollBar control
- scroll bars [Windows Forms], about scroll bars
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
ms.openlocfilehash: d4a7912a5781fc583357affa728f7d81059b5cf9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097312"
---
# <a name="hscrollbar-and-vscrollbar-controls-overview-windows-forms"></a>HScrollBar 控件和 VScrollBar 控件概述（Windows 窗体）
Windows 窗体<xref:System.Windows.Forms.ScrollBar>控制用于方便地在长列表项或大量的信息的任一水平或垂直滚动应用程序或控件。 滚动条是一种常见元素的 Windows 接口，因此<xref:System.Windows.Forms.ScrollBar>控件通常用于无法从元素派生的控件<xref:System.Windows.Forms.ScrollableControl>类。 同样，许多开发人员选择合并<xref:System.Windows.Forms.ScrollBar>控制创建其自己的用户控件时。  
  
 <xref:System.Windows.Forms.HScrollBar> （水平） 和<xref:System.Windows.Forms.VScrollBar>（垂直） 控件的其他控件的工作方式，并且具有其自己的事件、 属性和方法集。 <xref:System.Windows.Forms.ScrollBar> 控件不是附加到的文本框、 列表框、 组合框或 MDI 窗体的内置滚动条相同 (<xref:System.Windows.Forms.TextBox>控件具有<xref:System.Windows.Forms.TextBox.ScrollBars%2A>属性来显示或隐藏附加到控件的滚动条)。  
  
 <xref:System.Windows.Forms.ScrollBar>控件使用<xref:System.Windows.Forms.ScrollBar.Scroll>事件来监视沿滚动条的滚动框 （有时称为滚动块） 的移动。 使用<xref:System.Windows.Forms.ScrollBar.Scroll>事件提供了对滚动条值的访问，因为它正被拖动。  
  
## <a name="value-property"></a>Value 属性  
 <xref:System.Windows.Forms.ScrollBar.Value%2A>属性 （其中，默认情况下，为 0） 是`integer`滚动条中滚动框的位置相对应的值。 最小值的滚动框位置时，它将移到最左侧的位置 （对于水平滚动条） 或 （对于垂直滚动条） 的顶部位置。 当滚动框位于最大值、 滚动框移到最右侧或底部位置。 同样，值范围的顶部和底部之间的中间位置将前导边缘中间的滚动条的滚动框。  
  
 除了使用鼠标单击的滚动栏值更改，用户还可以拖动滚动框到沿条的任意点。 生成的值取决于滚动框的位置，但它始终位于范围内<xref:System.Windows.Forms.ScrollBar.Minimum%2A>到<xref:System.Windows.Forms.ScrollBar.Maximum%2A>由用户设置的属性。  
  
## <a name="largechange-and-smallchange-properties"></a>LargeChange 和 SmallChange 属性  
 当用户按下 PAGE UP 或 PAGE DOWN 键或单击中滚动框中，任意一侧的滚动条轨道<xref:System.Windows.Forms.ScrollBar.Value%2A>根据中设置的值的属性更改<xref:System.Windows.Forms.ScrollBar.LargeChange%2A>属性。  
  
 当用户按下一个箭头键或单击滚动条按钮时，之一<xref:System.Windows.Forms.ScrollBar.Value%2A>根据中设置的值的属性更改<xref:System.Windows.Forms.ScrollBar.SmallChange%2A>属性。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.HScrollBar>
- <xref:System.Windows.Forms.VScrollBar>
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
