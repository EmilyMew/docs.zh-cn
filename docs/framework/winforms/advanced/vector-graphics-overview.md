---
title: 向量图形概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inclusive-inclusive endpoints
- coordinate systems
- graphics [Windows Forms], vector graphics
ms.assetid: 0195df81-66be-452d-bb53-5a582ebfdc09
ms.openlocfilehash: d424254839db6c403bafe779f475c0e344918a5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087958"
---
# <a name="vector-graphics-overview"></a>向量图形概述
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 绘制线条、 矩形和其他形状的坐标系统上。 可以选择使用不同的坐标系统，但默认坐标系统中都具有原点左上角具有 x 轴指向右，y 轴指向下方。 默认坐标系统中的度量单位为像素。  
  
## <a name="the-building-blocks-of-gdi"></a>GDI + 的构建基块  
 ![矢量图形](./media/aboutgdip02-art01.gif "AboutGdip02_Art01")  
  
 计算机监视器上点称为图片元素或像素的矩形数组创建其显示。 有所不同到下一步，一台监视器显示在屏幕的像素数，并显示在单个监视器的像素数通常可某种程度上由用户。  
  
 ![矢量图形](./media/aboutgdip02-art02.gif "AboutGdip02_Art02")  
  
 当你使用[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]若要绘制线条、 矩形或曲线，提供有关要绘制的项的某些关键信息。 例如，可以通过提供两个点，指定的行，并可以通过提供一个点、 高度和宽度指定矩形。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 显示驱动程序软件，以确定哪些像素必须打开以显示行、 矩形或曲线结合工作。 下图显示了已打开，可以显示行的 （4，2） 的点到点 （12、 8） 的像素。  
  
 ![矢量图形](./media/aboutgdip02-art03.gif "AboutGdip02_Art03")  
  
 随着时间推移，某些基本构造块已被证明是最适用于创建二维图片。 这些构建基块，支持的[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]，给出了下面的列表：  
  
-   直线  
  
-   矩形  
  
-   省略号  
  
-   Arcs  
  
-   多边形  
  
-   基数样条  
  
-   贝塞尔曲线样条  
  
## <a name="methods-for-drawing-with-a-graphics-object"></a>进行绘制的图形对象的方法  
 <xref:System.Drawing.Graphics>类中[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供了用于绘制的项前面的列表中的以下方法： <xref:System.Drawing.Graphics.DrawLine%2A>， <xref:System.Drawing.Graphics.DrawRectangle%2A>， <xref:System.Drawing.Graphics.DrawEllipse%2A>， <xref:System.Drawing.Graphics.DrawPolygon%2A>， <xref:System.Drawing.Graphics.DrawArc%2A>， <xref:System.Drawing.Graphics.DrawCurve%2A> （适用于基本样条），并<xref:System.Drawing.Graphics.DrawBezier%2A>. 每种方法将重载;也就是说，每个方法支持多个不同的参数列表。 例如，一种<xref:System.Drawing.Graphics.DrawLine%2A>方法接收<xref:System.Drawing.Pen>对象和四个整数，而另一个变体<xref:System.Drawing.Graphics.DrawLine%2A>方法接收<xref:System.Drawing.Pen>对象和两个<xref:System.Drawing.Point>对象。  
  
 绘制线条、 矩形和贝塞尔自由绘制曲线的方法具有复数形式的伴随方法，可在单个调用中绘制多个项： <xref:System.Drawing.Graphics.DrawLines%2A>， <xref:System.Drawing.Graphics.DrawRectangles%2A>，和<xref:System.Drawing.Graphics.DrawBeziers%2A>。 此外，<xref:System.Drawing.Graphics.DrawCurve%2A>方法有一个随附方法<xref:System.Drawing.Graphics.DrawClosedCurve%2A>、，关闭曲线的曲线的结束点连接到的起始点。  
  
 绘制方法的所有<xref:System.Drawing.Graphics>类结合工作<xref:System.Drawing.Pen>对象。 若要绘制任何内容，必须创建至少两个对象：<xref:System.Drawing.Graphics>对象和一个<xref:System.Drawing.Pen>对象。 <xref:System.Drawing.Pen>对象将存储属性，例如线条宽度和颜色，要绘制的项。 <xref:System.Drawing.Pen>对象作为一个参数传递给绘图的方法。 例如，一种<xref:System.Drawing.Graphics.DrawLine%2A>方法接收<xref:System.Drawing.Pen>对象，如下面的示例绘制一个宽度为 100，高度为 50 到左上角的矩形中所示的四个整数 （20、 10）：  
  
 [!code-csharp[LinesCurvesAndShapes#11](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#11)]
 [!code-vb[LinesCurvesAndShapes#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [如何：创建用于绘制的 Graphics 对象](how-to-create-graphics-objects-for-drawing.md)
