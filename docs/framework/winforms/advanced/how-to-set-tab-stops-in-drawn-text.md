---
title: 如何：在绘制的文本中设置制表位
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 76431d34504b40a299200693735a0a989127d683
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832302"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>如何：在绘制的文本中设置制表位
可以通过调用设置文本的所有制表位<xref:System.Drawing.StringFormat.SetTabStops%2A>方法<xref:System.Drawing.StringFormat>对象，然后将其传递<xref:System.Drawing.StringFormat>对象传递给<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>类。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>不支持添加制表位与绘制的文本，尽管您可以扩展现有选项卡会停止使用的作用<xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType>标志。  
  
## <a name="example"></a>示例  
 下面的示例在 150、 250 和 350 设置制表位。 然后，代码显示选项卡式的列表的名称和测试分数。  
  
 下图显示的选项卡式的文本：  
  
 ![显示选项卡式的姓名和分数列表的屏幕截图。](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 以下代码将传递到两个参数<xref:System.Drawing.StringFormat.SetTabStops%2A>方法。 第二个参数是一个数组，包含制表位偏移量。 第一个参数传递给<xref:System.Drawing.StringFormat.SetTabStops%2A>为 0，指示数组中的第一个偏移量从边界的矩形的左边缘的位置 0，来度量。  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>编译代码  
  
-   前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>请参阅
- [使用字体和文本](using-fonts-and-text.md)
- [如何：用 GDI 绘制文本](how-to-draw-text-with-gdi.md)
