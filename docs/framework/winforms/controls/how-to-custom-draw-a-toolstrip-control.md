---
title: 如何：自定义绘制 ToolStrip 控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: d9a58dbaeae3f0cd165d72b8fd281b903ad9cca2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705744"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>如何：自定义绘制 ToolStrip 控件
<xref:System.Windows.Forms.ToolStrip> 控件具有以下关联的呈现（绘制）类：  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> 提供你使用的操作系统的外观和样式。  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 提供 Microsoft Office 的外观和样式。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> 是其他两个呈现类的抽象基类。  
  
 若要对 <xref:System.Windows.Forms.ToolStrip> 进行自定义绘制（也称为所有者描述），可以重写其中一个呈现器类，并更改呈现逻辑的一个方面。  
  
 下面的过程描述自定义绘制的各个方面。  
  
### <a name="to-switch-between-the-provided-renderers"></a>在提供的呈现器之间切换  
  
-   将 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 属性设置为所需的 <xref:System.Windows.Forms.ToolStripRenderMode> 值。  
  
     使用 <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>，静态 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> 为应用程序确定呈现器。 <xref:System.Windows.Forms.ToolStripRenderMode> 的其他值为 <xref:System.Windows.Forms.ToolStripRenderMode.Custom>、<xref:System.Windows.Forms.ToolStripRenderMode.Professional> 和 <xref:System.Windows.Forms.ToolStripRenderMode.System>。  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>将 Microsoft Office 样式边框更改为直线  
  
-   重写 <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>，但不调用基类。  
  
> [!NOTE]
>  此方法没有针对 <xref:System.Windows.Forms.ToolStripRenderer>、<xref:System.Windows.Forms.ToolStripSystemRenderer> 和 <xref:System.Windows.Forms.ToolStripProfessionalRenderer> 的版本。  
  
### <a name="to-change-the-professionalcolortable"></a>更改 ProfessionalColorTable  
  
-   重写 <xref:System.Windows.Forms.ProfessionalColorTable> 并更改所需的颜色。  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>更改应用程序中所有 ToolStrip 控件的呈现  
  
1.  使用 <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> 属性从提供的呈现器中选择一个。  
  
2.  使用 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> 分配自定义呈现器。  
  
3.  确保 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> 已设置为默认值 <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>。  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>关闭整个应用程序的 Microsoft Office 颜色  
  
-   将 <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> 设置为 `false`。  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>关闭一个 ToolStrip 控件的 Microsoft Office 颜色  
  
-   使用类似于以下代码示例的代码。  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [具有内置所有者描述支持的控件](controls-with-built-in-owner-drawing-support.md)
- [如何：创建并设置自定义呈现器在 Windows 窗体的 ToolStrip 控件](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [ToolStrip 控件概述](toolstrip-control-overview-windows-forms.md)
