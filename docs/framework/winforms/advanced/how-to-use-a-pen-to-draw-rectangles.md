---
title: 如何：使用钢笔绘制矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: 0e51a1e3a2d14754147dbd36f170127a7e978acd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074607"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>如何：使用钢笔绘制矩形
若要绘制矩形，需要<xref:System.Drawing.Graphics>对象和一个<xref:System.Drawing.Pen>对象。 <xref:System.Drawing.Graphics>对象提供<xref:System.Drawing.Graphics.DrawRectangle%2A>方法，和<xref:System.Drawing.Pen>对象将存储的行中，如颜色和宽度的功能。  
  
## <a name="example"></a>示例  
 下面的示例绘制一个具有在其左上角的矩形 （10，10）。 矩形的宽度为 100，50 的高度。 第二个参数传递给<xref:System.Drawing.Pen.%23ctor%2A>构造函数指示钢笔的宽度为 5 像素。  
  
 当绘制矩形时，触笔上居中显示矩形的边界。 矩形的边钢笔的宽度为 5，因为所绘制的 5 个像素宽，因此绘制该 1 像素上边界本身，2 个像素绘制内，和 2 个像素绘制在外部。 有关笔对齐方式的更多详细信息，请参阅[如何：设置笔的宽度和对齐方式](how-to-set-pen-width-and-alignment.md)。  
  
 下图显示了所得矩形的大小。 点线显示，其中矩形已绘制如果钢笔的宽度必须被一个像素。 矩形的左上角的放大的视图显示胖黑色线条在这些点线上居中。  
  
 ![显示在绘制的矩形使用黑色和虚线的屏幕截图。](./media/how-to-use-a-pen-to-draw-rectangles/drawn-rectangle-black-lines-dotted-lines.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>编译代码  
 前面的示例专用于 Windows 窗体，并且它需要<xref:System.Windows.Forms.PaintEventArgs>`e`，这是一个参数的<xref:System.Windows.Forms.Control.Paint>事件处理程序。  
  
## <a name="see-also"></a>请参阅

- [使用钢笔绘制线条和形状](using-a-pen-to-draw-lines-and-shapes.md)
