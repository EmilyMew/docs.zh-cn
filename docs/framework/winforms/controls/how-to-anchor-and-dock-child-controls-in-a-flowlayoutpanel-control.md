---
title: 如何：锚定和停靠子控件在 FlowLayoutPanel 控件中
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 62cc25b705b382e1f4ef32ae6889df785a6a9173
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709904"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>如何：锚定和停靠子控件在 FlowLayoutPanel 控件中
<xref:System.Windows.Forms.FlowLayoutPanel> 控件支持其子控件中的 <xref:System.Windows.Forms.Control.Anchor%2A> 和 <xref:System.Windows.Forms.Control.Dock%2A> 属性。  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>在 FlowLayoutPanel 控件中锚定和停靠子控件  
  
1.  在窗体上创建一个 <xref:System.Windows.Forms.FlowLayoutPanel> 控件。  
  
2.  设置<xref:System.Windows.Forms.Control.Width%2A>的<xref:System.Windows.Forms.FlowLayoutPanel>控制对**300**，并设置其<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>到<xref:System.Windows.Forms.FlowDirection.TopDown>。  
  
3.  创建两个 <xref:System.Windows.Forms.Button> 控件，并将它们放入 <xref:System.Windows.Forms.FlowLayoutPanel> 控件中。  
  
4.  设置<xref:System.Windows.Forms.Control.Width%2A>到第一个按钮**200**。  
  
5.  将第二个按钮的 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为 <xref:System.Windows.Forms.DockStyle.Fill>。  
  
    > [!NOTE]
    >  第二个按钮采用与第一个按钮相同的宽度。 它不在 <xref:System.Windows.Forms.FlowLayoutPanel> 控件的宽度范围内拉伸。  
  
6.  将第二个按钮的 <xref:System.Windows.Forms.Control.Dock%2A> 属性设置为 `None`。 这将导致该按钮采用其原始的宽度。  
  
7.  将第二个按钮的 <xref:System.Windows.Forms.Control.Anchor%2A> 属性设置为 `Left, Right`。  
  
    > [!IMPORTANT]
    >  第二个按钮采用与第一个按钮相同的宽度。 它不在 <xref:System.Windows.Forms.FlowLayoutPanel> 控件的宽度范围内拉伸。 这是在 <xref:System.Windows.Forms.FlowLayoutPanel> 控件中锚定和停靠的一般规则：对于垂直流方向，<xref:System.Windows.Forms.FlowLayoutPanel> 控件计算列中最宽子控件的隐含列的宽度。 对齐或拉伸此列中具有 <xref:System.Windows.Forms.Control.Anchor%2A> 或 <xref:System.Windows.Forms.Control.Dock%2A> 属性的所有其他控件以适合此隐含列。 该行为以相似的方式在水平流方向工作。 <xref:System.Windows.Forms.FlowLayoutPanel> 控件计算行中最高子控件的隐含行的高度，并对齐此行中所有停靠的或锚定的子控件或调整其大小以适应隐含行。  
  
## <a name="example"></a>示例  
 下图显示了四个按钮，它们相对于 <xref:System.Windows.Forms.FlowLayoutPanel> 中的蓝色按钮锚定和停靠。 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 为 <xref:System.Windows.Forms.FlowDirection.LeftToRight>。  
  
 ![FlowLayoutPanel 锚定](./media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 下图显示了四个按钮，它们相对于 <xref:System.Windows.Forms.FlowLayoutPanel> 中的蓝色按钮锚定和停靠。 <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> 为 <xref:System.Windows.Forms.FlowDirection.TopDown>。  
  
 ![FlowLayoutPanel 锚定](./media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 以下代码示例演示了 <xref:System.Windows.Forms.FlowLayoutPanel> 控件中 <xref:System.Windows.Forms.Button> 控件的各种 <xref:System.Windows.Forms.Control.Anchor%2A> 属性的值。  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System、System.Data、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [FlowLayoutPanel 控件概述](flowlayoutpanel-control-overview.md)
