---
title: 如何：在 ToolStrip 控件中使用工具提示
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 884fb75d53e425702cdef46615a16394b835518f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076464"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>如何：在 ToolStrip 控件中使用工具提示
可以显示<xref:System.Windows.Forms.ToolTip>有关<xref:System.Windows.Forms.ToolStrip>想通过设置控件的控件<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>属性设置为`true`。  
  
### <a name="to-display-a-tooltip"></a>若要显示的工具提示  
  
-   设置<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>到控件属性`true`。  
  
     默认值<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>是`true`，默认值的<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>并<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>是`false`。  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>若要使用的工具提示文本的 ToolStripButton ToolTipText 属性  
  
1.  设置<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>属性的按钮为`true`。  
  
2.  设置<xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>属性的按钮为`false`。  
  
     `AutoToolTip`属性是`true`对于默认情况下<xref:System.Windows.Forms.ToolStripButton>， <xref:System.Windows.Forms.ToolStripDropDownButton>，和<xref:System.Windows.Forms.ToolStripSplitButton>。  
  
     一个<xref:System.Windows.Forms.ToolStripButton>使用其`Text`属性<xref:System.Windows.Forms.ToolTip>默认情况下的文本。 使用此过程用于显示自定义文本<xref:System.Windows.Forms.ToolStripButton><xref:System.Windows.Forms.ToolTip>。  
  
> [!NOTE]
>  如果您设置<xref:System.Windows.Forms.ToolStripItemDisplayStyle>到<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>或<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>，没有文本将出现在按钮，但仍将显示工具提示。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [ToolStrip 控件概述](toolstrip-control-overview-windows-forms.md)
