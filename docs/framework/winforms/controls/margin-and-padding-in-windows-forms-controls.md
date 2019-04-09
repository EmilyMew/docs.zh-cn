---
title: Windows 窗体控件中的边距和填充
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: bf1f88f6efcedd740bff92dda391470391f16ce5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094043"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a>Windows 窗体控件中的边距和填充
在窗体上精确地放置控件对于许多应用程序而言是高优先级。 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空间给你提供许多布局功能来实现此目的。 其中两个最重要的功能是 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 属性。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> 属性定义控件周围的空间，该空间使其他控件与该控件的边框保持指定的距离。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> 属性定义控件内部的空间，该空间使控件的内容（例如，其 <xref:System.Windows.Forms.Control.Text%2A> 属性的值）与该控件的边框保持指定的距离。  
  
 下图显示控件上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 属性。  
  
 ![填充和边距的 Windows 窗体控件](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 Visual Studio 中具有对此功能的设计时支持。 另请参阅[演练：对 Windows 窗体控件使用 Padding、 Margins 和 AutoSize 属性](windows-forms-controls-padding-autosize.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
