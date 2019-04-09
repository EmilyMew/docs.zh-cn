---
title: GDI+ 中的笔、直线和矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 84752773c0b56d9684dc31620d463d4ddccf9dad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078221"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>GDI+ 中的笔、直线和矩形
若要绘制的线条[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]你需要创建<xref:System.Drawing.Graphics>对象和一个<xref:System.Drawing.Pen>对象。 <xref:System.Drawing.Graphics>对象提供的实际执行绘制操作的方法和<xref:System.Drawing.Pen>对象将存储属性，例如线条颜色、 宽度和样式。  
  
## <a name="drawing-a-line"></a>绘制一条线  
 若要绘制一条线，请调用<xref:System.Drawing.Graphics.DrawLine%2A>方法的<xref:System.Drawing.Graphics>对象。 <xref:System.Drawing.Pen>对象作为一个自变量传递<xref:System.Drawing.Graphics.DrawLine%2A>方法。 下面的示例将行从点 （4，2） 绘制到点 （12，6）：  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> 是一种重载的方法<xref:System.Drawing.Graphics>类，因此有几种方法可以提供该文件使用的参数。 例如，构造两个<xref:System.Drawing.Point>对象并传递<xref:System.Drawing.Point>对象作为自变量到<xref:System.Drawing.Graphics.DrawLine%2A>方法：  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>构造笔  
 在构造时，可以指定某些属性<xref:System.Drawing.Pen>对象。 例如，一个`Pen`构造函数允许您指定颜色和宽度。 下面的示例绘制一条蓝线的宽度为 2 从 （0，0） 到 （60，30）：  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>虚线和线帽  
 <xref:System.Drawing.Pen>对象还公开属性，如<xref:System.Drawing.Pen.DashStyle%2A>，可用于指定行的功能。 下面的示例绘制虚线从 （100，50） 到 （300，80）：  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 可以使用的属性<xref:System.Drawing.Pen>对象，以设置行的更多属性。 <xref:System.Drawing.Pen.StartCap%2A>和<xref:System.Drawing.Pen.EndCap%2A>属性指定线条的端点的外观; 平面、 方形、 向上舍入、 三角形，可以是在结束或自定义形状。 <xref:System.Drawing.Pen.LineJoin%2A>属性，可以指定连接的直线是斜 （联接以尖角）、 倾斜、 舍入，还是剪裁。 下图显示了具有线帽和联接的各种样式的行。  
  
 ![Lines](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>绘制一个矩形  
 绘制矩形[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]类似于绘制线条。 若要绘制一个矩形，需要<xref:System.Drawing.Graphics>对象和一个<xref:System.Drawing.Pen>对象。 <xref:System.Drawing.Graphics>对象提供<xref:System.Drawing.Graphics.DrawRectangle%2A>方法，和<xref:System.Drawing.Pen>对象将存储属性，例如线条宽度和颜色。 <xref:System.Drawing.Pen>对象作为一个自变量传递<xref:System.Drawing.Graphics.DrawRectangle%2A>方法。 下面的示例绘制一个具有在其左上角的矩形 （100，50），宽度为 80，和高度为 40:  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> 是一种重载的方法<xref:System.Drawing.Graphics>类，因此有几种方法可以提供该文件使用的参数。 例如，可以构造<xref:System.Drawing.Rectangle>对象并将传递<xref:System.Drawing.Rectangle>对象传递给<xref:System.Drawing.Graphics.DrawRectangle%2A>作为参数的方法：  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 一个<xref:System.Drawing.Rectangle>对象有方法和属性用于操作和收集有关该矩形的信息。 例如，<xref:System.Drawing.Rectangle.Inflate%2A>和<xref:System.Drawing.Rectangle.Offset%2A>方法更改的大小和位置的矩形。 <xref:System.Drawing.Rectangle.IntersectsWith%2A>方法指示矩形是否与另一个给定矩形和<xref:System.Drawing.Rectangle.Contains%2A>方法告诉您给定时的点是位于矩形内。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [如何：创建钢笔](how-to-create-a-pen.md)
- [如何：在 Windows 窗体上绘制直线](how-to-draw-a-line-on-a-windows-form.md)
- [如何：绘制轮廓形状](how-to-draw-an-outlined-shape.md)
