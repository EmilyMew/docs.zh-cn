---
title: GDI+ 中的多边形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: 2b1e3d387e4d056d9187c54dcef560544206c370
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132621"
---
# <a name="polygons-in-gdi"></a>GDI+ 中的多边形
多边形是闭合的形状有三个或多个直条边。 例如，一个三角形是利用三边的多边形、 矩形是具有四个边的多边形和一个五边形是有五条边的多边形。 下图显示了几个多边形。  
  
 ![Polygons](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>绘制多边形  
 若要绘制多边形，需要<xref:System.Drawing.Graphics>对象，<xref:System.Drawing.Pen>对象和数组<xref:System.Drawing.Point>(或<xref:System.Drawing.PointF>) 对象。 <xref:System.Drawing.Graphics>对象提供<xref:System.Drawing.Graphics.DrawPolygon%2A>方法。 <xref:System.Drawing.Pen>对象将存储属性，例如宽度和颜色，用来呈现多边形、 和的数组的行<xref:System.Drawing.Point>对象将存储要由直线连接的点。 <xref:System.Drawing.Pen>对象和数组<xref:System.Drawing.Point>对象将作为参数传递给<xref:System.Drawing.Graphics.DrawPolygon%2A>方法。 下面的示例绘制三边的多边形。 请注意，只有三个点中的`myPointArray`:（0，0） （50，30） 和 （30、 60）。 <xref:System.Drawing.Graphics.DrawPolygon%2A>方法会自动关闭多边形通过绘制中的一行 （30、 60） 返回到起始点 （0，0）。  
  
 [!code-csharp[LinesCurvesAndShapes#111](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 下图显示了多边形。  
  
 ![Polygon](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [如何：创建钢笔](how-to-create-a-pen.md)
