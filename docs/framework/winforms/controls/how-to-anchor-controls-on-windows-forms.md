---
title: 如何：在 Windows 窗体上锚定控件
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: 28cee4e1aa989ef4df902907c09645a1a0400475
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072984"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>如何：在 Windows 窗体上锚定控件
设计用户可以在运行时调整大小的窗体时，如果你的窗体上的控件应调整大小并正确地重新定位。 若要调整动态处理该窗体控件的大小，可以使用<xref:System.Windows.Forms.Control.Anchor%2A>Windows 窗体控件的属性。 <xref:System.Windows.Forms.Control.Anchor%2A>属性定义控件的定位点位置。 当控件锚定到窗体和窗体调整时，控件将保持该控件的定位点位置之间的距离。 例如，如果你有<xref:System.Windows.Forms.TextBox>控件的窗体调整大小时，定位到左侧、 右侧和底部边缘与窗体，<xref:System.Windows.Forms.TextBox>水平控件调整大小时，以便保持与窗体的右侧和左侧边的距离相同。 此外，该控件垂直定位其自身，以便其位置始终是与窗体的下边缘的距离相同。 如果控件未锚定和调整窗体，则更改控件相对于窗体的边缘的位置。  
  
 <xref:System.Windows.Forms.Control.Anchor%2A>与属性交互<xref:System.Windows.Forms.Control.AutoSize%2A>属性。 有关详细信息，请参阅[AutoSize 属性概述](autosize-property-overview.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-anchor-a-control-on-a-form"></a>若要定位到窗体上控件  
  
1.  选择你想要定位的控件。  
  
    > [!NOTE]
    >  您可以通过按住 CTRL 键，单击每个控件以选择它，然后按照此过程的其余部分同时定位多个控件。  
  
2.  在中**属性**窗口中，单击右侧的箭头<xref:System.Windows.Forms.Control.Anchor%2A>属性。  
  
     显示一个编辑器，显示十字形。  
  
3.  若要设置定位点，请单击上、 左、 右或十字线的下半部分。  
  
     控件锚定到顶部，并且默认情况下保留。  
  
4.  若要清除已定位的控件的一侧，单击跨该 arm。  
  
5.  若要关闭<xref:System.Windows.Forms.Control.Anchor%2A>属性编辑器中，单击<xref:System.Windows.Forms.Control.Anchor%2A>再次属性名称。  
  
 当在运行时显示窗体时，该控件调整大小，以保持与窗体的边缘的距离相同不变。 定位边缘的距离始终保持不变所定义的距离时将控件置于 Windows 窗体设计器。  
  
> [!NOTE]
>  某些控件，如<xref:System.Windows.Forms.ComboBox>控件，为其高度的限制。 锚定到其窗体或容器的底部的控件不能强制超过其高度限制的控件。  
  
 继承的控件必须是`Protected`能够定位。 若要更改控件的访问级别，设置其`Modifiers`中的属性**属性**窗口。  
  
## <a name="see-also"></a>请参阅

- [Windows 窗体控件](index.md)
- [排列 Windows 窗体上的控件](arranging-controls-on-windows-forms.md)
- [AutoSize 属性概述](autosize-property-overview.md)
- [如何：在 Windows 窗体上停靠控件](how-to-dock-controls-on-windows-forms.md)
- [演练：使用 FlowLayoutPanel 在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [演练：使用 TableLayoutPanel 在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [演练：使用 Padding、Margins 和 AutoSize 属性对 Windows 窗体控件进行布局](windows-forms-controls-padding-autosize.md)
