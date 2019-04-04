---
title: 如何：显示靠一侧对齐选项卡使用 tabcontrol 控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
ms.openlocfilehash: 8715cb1a1f0d5795afc4003afcecdb3fb89912c3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705177"
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>如何：显示靠一侧对齐选项卡使用 tabcontrol 控件
<xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.Alignment%2A> 属性支持垂直显示选项卡（沿控件的左边缘或右边缘），而不是水平显示（沿控件的顶部或底部）。 默认情况下，此垂直显示会造成不良的用户体验，因为当视觉样式启用时，<xref:System.Windows.Forms.TabPage> 对象的 <xref:System.Windows.Forms.TabPage.Text%2A> 属性不显示在选项卡中。 此外，也没有直接的方法来控制选项卡内文本的方向。可以使用 <xref:System.Windows.Forms.TabControl> 的所有者描述来改善此体验。  
  
 下面的过程演示如何使用“所有者描述”功能呈现右对齐的选项卡（选项卡文本的运行方向从左到右）。  
  
### <a name="to-display-right-aligned-tabs"></a>显示右对齐的选项卡  
  
1.  在窗体中添加 <xref:System.Windows.Forms.TabControl>。  
  
2.  将 <xref:System.Windows.Forms.TabControl.Alignment%2A> 属性设置为 <xref:System.Windows.Forms.TabAlignment.Right>。  
  
3.  将 <xref:System.Windows.Forms.TabControl.SizeMode%2A> 属性设置为 <xref:System.Windows.Forms.TabSizeMode.Fixed>，以以使所有选项卡具有相同的宽度。  
  
4.  将 <xref:System.Windows.Forms.TabControl.ItemSize%2A> 属性设置为选项卡的首选固定大小。 请记住，<xref:System.Windows.Forms.TabControl.ItemSize%2A> 属性的行为如同选项卡位于顶部时的行为一样，尽管它们是右对齐的。 因此，为了增加选项卡宽度，必须更改 <xref:System.Drawing.Size.Height%2A> 属性；为了增加选项卡高度，必须更改 <xref:System.Drawing.Size.Width%2A> 属性。  
  
     在下面的代码示例中，将选项卡的 <xref:System.Drawing.Size.Width%2A> 设置为 25，<xref:System.Drawing.Size.Height%2A> 设置为 100 可得到最佳结果。  
  
5.  将 <xref:System.Windows.Forms.TabControl.DrawMode%2A> 属性设置为 <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>。  
  
6.  为从左到右呈现文本的 <xref:System.Windows.Forms.TabControl> 的 <xref:System.Windows.Forms.TabControl.DrawItem> 事件定义一个处理程序。  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](~/samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>请参阅
- [TabControl 控件](tabcontrol-control-windows-forms.md)
