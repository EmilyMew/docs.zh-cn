---
title: 如何：在指定位置绘制文本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: 8327043f9afdec7e2d84e564801342d7d7cbef9d
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412235"
---
# <a name="how-to-draw-text-at-a-specified-location"></a>如何：在指定位置绘制文本
在执行自定义绘图时，可以从指定位置开始的一个水平行中绘制文本。 可以通过使用这种方式绘制文本<xref:System.Drawing.Graphics.DrawString%2A>重载的方法<xref:System.Drawing.Graphics>采用类<xref:System.Drawing.Point>或<xref:System.Drawing.PointF>参数。 <xref:System.Drawing.Graphics.DrawString%2A>方法还需要<xref:System.Drawing.Brush>和 <xref:System.Drawing.Font>  
  
 此外可以使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>重载的方法<xref:System.Windows.Forms.TextRenderer>采用<xref:System.Drawing.Point>。 <xref:System.Windows.Forms.TextRenderer.DrawText%2A> 此外需要<xref:System.Drawing.Color>和一个<xref:System.Drawing.Font>。  
  
 下图显示了在使用时，在指定点绘制文本的输出<xref:System.Drawing.Graphics.DrawString%2A>重载的方法。  
  
 ![指定点处显示的文本输出的屏幕截图。](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>若要绘制一行使用 GDI + 文本  
  
1.  使用<xref:System.Drawing.Graphics.DrawString%2A>方法，并传递所需的文本<xref:System.Drawing.Point>或<xref:System.Drawing.PointF>， <xref:System.Drawing.Font>，和<xref:System.Drawing.Brush>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a>若要绘制用 GDI 的文本行  
  
1.  使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>方法，并传递所需的文本<xref:System.Drawing.Point>， <xref:System.Drawing.Font>，和<xref:System.Drawing.Color>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例需要：  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`这是一个参数的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>请参阅
- [如何：用 GDI 绘制文本](how-to-draw-text-with-gdi.md)
- [使用字体和文本](using-fonts-and-text.md)
- [如何：构造字体系列和字体](how-to-construct-font-families-and-fonts.md)
- [如何：在矩形中绘制换行文本](how-to-draw-wrapped-text-in-a-rectangle.md)
