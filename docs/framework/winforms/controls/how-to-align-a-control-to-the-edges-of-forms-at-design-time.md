---
title: 如何：在设计时将控件与窗体边缘对齐
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: 8f74a6b56e99e016bfb27bbe1b271f6c71af8f87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140889"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>如何：在设计时将控件与窗体边缘对齐
可以使控件与窗体的边缘对齐通过设置<xref:System.Windows.Forms.Control.Dock%2A>。 此属性指定控件在窗体中的驻留位置。 可以将 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为下列值：  
  
|设置|控件上的效果|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|停靠到窗体底部。|  
|<xref:System.Windows.Forms.DockStyle.Fill>|占据窗体中的所有剩余空间。|  
|<xref:System.Windows.Forms.DockStyle.Left>|停靠到窗体的左侧。|  
|<xref:System.Windows.Forms.DockStyle.None>|执行停靠任何位置，而是显示在指定的位置及其<xref:System.Windows.Forms.Control.Location%2A>。|  
|<xref:System.Windows.Forms.DockStyle.Right>|停靠到窗体的右侧。|  
|<xref:System.Windows.Forms.DockStyle.Top>|停靠到窗体的顶部。|  
  
 此外可以在代码中设置这些值。 有关详细信息，请参阅[如何：将控件与窗体边缘对齐](how-to-align-a-control-to-the-edges-of-forms.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a>若要在设计时设置控件的 Dock 属性  
  
1.  在 Windows 窗体设计器中，选择您的控件。  
  
2.  在中**属性**窗口中，单击下拉列表框旁边的<xref:System.Windows.Forms.Control.Dock%2A>属性。  
  
     表示六种可能的图形界面<xref:System.Windows.Forms.Control.Dock%2A>显示设置。  
  
3.  选择合适的设置。  
  
4.  您的控件现在将停靠的设置指定的方式。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [如何：使控件与窗体边缘对齐](how-to-align-a-control-to-the-edges-of-forms.md)
- [演练：使用对齐线在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [如何：在 Windows 窗体上锚定控件](how-to-anchor-controls-on-windows-forms.md)
- [如何：在 TableLayoutPanel 控件中锚定和停靠子控件](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [如何：在 FlowLayoutPanel 控件中锚定和停靠子控件](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [演练：使用 TableLayoutPanel 在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [演练：使用 FlowLayoutPanel 在 Windows 窗体上排列控件](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [设计时开发 Windows 窗体控件](developing-windows-forms-controls-at-design-time.md)
