---
title: 如何：在矩形中绘制换行文本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: 35eca2fc0fe40db1b590f4c599baee01c9a9faf3
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654520"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a>如何：在矩形中绘制换行文本
可以通过使用在矩形中绘制换行的文本<xref:System.Drawing.Graphics.DrawString%2A>重载的方法<xref:System.Drawing.Graphics>采用类<xref:System.Drawing.Rectangle>或<xref:System.Drawing.RectangleF>参数。 你还将使用<xref:System.Drawing.Brush>和一个<xref:System.Drawing.Font>。  
  
 您还可以绘制换行的文本在矩形中通过使用<xref:System.Windows.Forms.TextRenderer.DrawText%2A>重载的方法<xref:System.Windows.Forms.TextRenderer>采用<xref:System.Drawing.Rectangle>和一个<xref:System.Windows.Forms.TextFormatFlags>参数。 你还将使用<xref:System.Drawing.Color>和一个<xref:System.Drawing.Font>。  
  
 下图显示了当你使用的矩形中绘制文本的输出<xref:System.Drawing.Graphics.DrawString%2A>方法：
  
 ![显示时使用 DrawString 方法的输出的屏幕截图。](./media/how-to-draw-wrapped-text-in-a-rectangle/drawstring-method-font-text.png)  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>若要绘制换行中使用 GDI + 矩形文本  
  
1.  使用<xref:System.Drawing.Graphics.DrawString%2A>重载方法，并传递所需的文本<xref:System.Drawing.Rectangle>或<xref:System.Drawing.RectangleF>，<xref:System.Drawing.Font>和<xref:System.Drawing.Brush>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a>绘制换行文本中用 GDI 矩形  
  
1.  使用<xref:System.Windows.Forms.TextFormatFlags>枚举值指定的文本应与包装<xref:System.Windows.Forms.TextRenderer.DrawText%2A>重载方法，并传递所需的文本<xref:System.Drawing.Rectangle>，<xref:System.Drawing.Font>和<xref:System.Drawing.Color>。  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例需要：  
  
-   <xref:System.Windows.Forms.PaintEventArgs> `e`这是一个参数的<xref:System.Windows.Forms.PaintEventHandler>。  
  
## <a name="see-also"></a>请参阅
- [如何：用 GDI 绘制文本](how-to-draw-text-with-gdi.md)
- [使用字体和文本](using-fonts-and-text.md)
- [如何：构造字体系列和字体](how-to-construct-font-families-and-fonts.md)
- [如何：在指定位置绘制文本](how-to-draw-text-at-a-specified-location.md)
