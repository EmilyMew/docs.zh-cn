---
title: B&#233;zier GDI + 中的样条
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107323"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;zier GDI + 中的样条
贝塞尔样条是由四个点指定的曲线： 两个终结点 （p1 和 p2） 和两个控点 （c1 和 c2）。 曲线开始于 p1 和 p2 结束。 曲线不会经历的控点，但控制点的作用像磁铁一样，在某些方向上拉拽曲线并影响曲线弯曲的方式。 下图显示了其终结点和控制点一个贝塞尔曲线。  
  
 ![贝塞尔自由绘制曲线](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 曲线开始 p1，会向管理点 c1 移动。 为在 p1 曲线的切线是从 p1 到 c1 绘制的行。 终结点 p2 处的切线是从 c2 到 p2 绘制的行。  
  
## <a name="drawing-bzier-splines"></a>绘制贝塞尔自由绘制曲线  
 若要绘制的贝塞尔样条，您需要的实例<xref:System.Drawing.Graphics>类和一个<xref:System.Drawing.Pen>。 实例<xref:System.Drawing.Graphics>类提供了<xref:System.Drawing.Graphics.DrawBezier%2A>方法，和<xref:System.Drawing.Pen>存储属性，例如宽度和颜色，用来呈现曲线的行。 <xref:System.Drawing.Pen>作为自变量之一传递<xref:System.Drawing.Graphics.DrawBezier%2A>方法。 其余的参数传递给<xref:System.Drawing.Graphics.DrawBezier%2A>方法是将终结点与管理点。 下面的示例绘制的起始点 （0，0） 的贝塞尔样条控制点 （40，20） 和 （80、 150） 和结束点 （10）：  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 下图显示了曲线、 控制点和两条切线。  
  
 ![贝塞尔自由绘制曲线](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 贝塞尔自由绘制曲线最初开发通过圣皮埃尔贝塞尔汽车行业中的设计。 它们已被公认为许多类型的计算机辅助设计中很有用，也用于定义字体的大纲。 贝塞尔样条可以产生各种形状，其中一些在下图中所示。  
  
 ![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [构造并绘制曲线](constructing-and-drawing-curves.md)
- [如何：创建用于绘制的 Graphics 对象](how-to-create-graphics-objects-for-drawing.md)
- [如何：创建钢笔](how-to-create-a-pen.md)
