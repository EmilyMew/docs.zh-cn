---
title: GDI+ 中的图形路径
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: c9a43065210f5ef0fffcae01cc7eb88349696b6b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140499"
---
# <a name="graphics-paths-in-gdi"></a>GDI+ 中的图形路径
路径是通过将线条、 矩形和简单的曲线相结合形成的。 还记得[向量图形概述](vector-graphics-overview.md)以下基本构建基块已证明是最适用于绘制图片：  
  
-   直线  
  
-   矩形  
  
-   省略号  
  
-   Arcs  
  
-   多边形  
  
-   基数样条  
  
-   贝塞尔自由绘制曲线  
  
 在 GDI + 中，<xref:System.Drawing.Drawing2D.GraphicsPath>对象允许你收集到单个单元的一系列这些构建基块。 然后可调用一次绘制线条、 矩形、 多边形和曲线的整个序列<xref:System.Drawing.Graphics.DrawPath%2A>方法的<xref:System.Drawing.Graphics>类。 下图显示了通过结合一行、 一段弧线、 贝塞尔样条和的基数样条创建的路径。  
  
 ![Path](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>使用路径  
 <xref:System.Drawing.Drawing2D.GraphicsPath>类提供了用于创建一系列要绘制的项的以下方法： <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> （对于基本样条），和<xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>。 每种方法将重载;也就是说，每个方法支持多个不同的参数列表。 例如，一种<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>方法将收到四个整数和的另一种变体<xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>方法接收两个<xref:System.Drawing.Point>对象。  
  
 添加到路径的线条、 矩形和贝塞尔自由绘制曲线的方法具有复数形式的伴随方法，可将多个项添加到单个调用中的路径： <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>， <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>，和<xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>。 此外，<xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>并<xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>方法有伴随方法<xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A>和<xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>，将闭合的曲线或饼图添加到路径。  
  
 若要绘制的路径，你需要<xref:System.Drawing.Graphics>对象，<xref:System.Drawing.Pen>对象，和一个<xref:System.Drawing.Drawing2D.GraphicsPath>对象。 <xref:System.Drawing.Graphics>对象提供<xref:System.Drawing.Graphics.DrawPath%2A>方法，和<xref:System.Drawing.Pen>对象将存储属性，例如宽度和用于呈现路径的线条颜色。 <xref:System.Drawing.Drawing2D.GraphicsPath>对象将存储的一系列直线和曲线构成的路径。 <xref:System.Drawing.Pen>对象和<xref:System.Drawing.Drawing2D.GraphicsPath>对象将作为参数传递给<xref:System.Drawing.Graphics.DrawPath%2A>方法。 下面的示例绘制线条、 椭圆和的贝塞尔样条组成的路径：  
  
 [!code-csharp[LinesCurvesAndShapes#101](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 下图显示的路径。  
  
 ![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 除了添加线条、 矩形和曲线的路径，可以将路径添加到路径。 这可以合并现有路径以形成复杂的长路径。  
  
 [!code-csharp[LinesCurvesAndShapes#102](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 有两个可以向路径添加其他项： 字符串和饼图。 饼图是内部的椭圆的一部分。 下面的示例创建一个路径，从一段弧线、 基数样条、 字符串和饼图：  
  
 [!code-csharp[LinesCurvesAndShapes#103](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 下图显示的路径。 请注意，路径不需要连接;分隔弧线、 基数样条、 字符串和饼图。  
  
 ![Paths](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [如何：创建用于绘制的 Graphics 对象](how-to-create-graphics-objects-for-drawing.md)
- [构造并绘制轨迹](constructing-and-drawing-paths.md)
