---
title: 如何：绘制序列的 B&#233;zier 自由绘制曲线
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 2b74b03137d5a450fb1e436a514877d1a17229ad
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654245"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>如何：绘制序列的 B&#233;zier 自由绘制曲线
可以使用<xref:System.Drawing.Graphics.DrawBeziers%2A>方法的<xref:System.Drawing.Graphics>类要绘制一系列连接贝塞尔自由绘制曲线。  
  
## <a name="example"></a>示例  
 下面的示例绘制包含两个已连接的贝塞尔样条曲线。 第一个贝塞尔样条的终结点是第二个贝塞尔自由绘制曲线的起始点。  
  
 下图显示了七个点以及已连接的自由绘制曲线：  
  
 ![图形的显示七个点以及已连接的样条。](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs> `e`，这是一个参数的<xref:System.Windows.Forms.Control.Paint>事件处理程序。  
  
## <a name="see-also"></a>请参阅
- [Windows 窗体中的图形和绘制](graphics-and-drawing-in-windows-forms.md)
- [GDI+ 中的贝塞尔自由绘制曲线](bezier-splines-in-gdi.md)
- [构造并绘制曲线](constructing-and-drawing-curves.md)
