---
title: GDI+ 中的椭圆和弧线
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 8bbc2eda6450128eac55576259880e83f07099ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117451"
---
# <a name="ellipses-and-arcs-in-gdi"></a>GDI+ 中的椭圆和弧线
您可以轻松地绘制椭圆和弧线使用<xref:System.Drawing.Graphics.DrawEllipse%2A>并<xref:System.Drawing.Graphics.DrawArc%2A>方法的<xref:System.Drawing.Graphics>类。  
  
## <a name="drawing-an-ellipse"></a>绘制椭圆  
 若要绘制一个椭圆，需要<xref:System.Drawing.Graphics>对象和一个<xref:System.Drawing.Pen>对象。 <xref:System.Drawing.Graphics>对象提供<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，和<xref:System.Drawing.Pen>对象将存储属性，例如宽度和颜色，用来呈现椭圆的行。 <xref:System.Drawing.Pen>对象作为一个自变量传递<xref:System.Drawing.Graphics.DrawEllipse%2A>方法。 其余的参数传递给<xref:System.Drawing.Graphics.DrawEllipse%2A>方法指定角的椭圆的边框。 下图显示一个椭圆，以及其边界的矩形。  
  
 ![椭圆和弧线](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 下面的示例绘制一个椭圆;边界矩形具有宽度为 80，高度为 40 和的左上角 （100，50）：  
  
 [!code-csharp[LinesCurvesAndShapes#51](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> 是一种重载的方法<xref:System.Drawing.Graphics>类，因此有几种方法可以提供该文件使用的参数。 例如，可以构造<xref:System.Drawing.Rectangle>并传递<xref:System.Drawing.Rectangle>到<xref:System.Drawing.Graphics.DrawEllipse%2A>作为参数的方法：  
  
 [!code-csharp[LinesCurvesAndShapes#52](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>绘制一段弧线，  
 一段弧线的椭圆的一部分。 若要绘制一段弧线，则调用<xref:System.Drawing.Graphics.DrawArc%2A>方法的<xref:System.Drawing.Graphics>类。 参数<xref:System.Drawing.Graphics.DrawArc%2A>方法将与参数的相同<xref:System.Drawing.Graphics.DrawEllipse%2A>方法，不同之处在于<xref:System.Drawing.Graphics.DrawArc%2A>需要起始角度和扫描角度。 下面的示例绘制一段弧线，使用 30 度的起始角度和扫描角度为 180 度：  
  
 [!code-csharp[LinesCurvesAndShapes#53](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 下图显示了弧线、 椭圆和边界的矩形。  
  
 ![椭圆和弧线](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [如何：创建用于绘制的 Graphics 对象](how-to-create-graphics-objects-for-drawing.md)
- [如何：创建钢笔](how-to-create-a-pen.md)
- [如何：绘制轮廓形状](how-to-draw-an-outlined-shape.md)
