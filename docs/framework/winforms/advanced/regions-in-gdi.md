---
title: GDI+ 中的区域
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, regions
- drawing [Windows Forms], regions
- regions
ms.assetid: 52184f9b-16dd-4bbd-85be-029112644ceb
ms.openlocfilehash: 33d4f4ecca7b9d777fa4eab5b6d031de10f03ccc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076016"
---
# <a name="regions-in-gdi"></a>GDI+ 中的区域
区域是输出设备的显示区域的一部分。 区域可以是简单 （一个矩形） 或复杂 （多边形和闭合的曲线的组合）。 下图显示了两个区域： 一个从一个矩形、 构造和路径中的其他构造。  
  
 ![Regions](./media/aboutgdip02-art27.gif "AboutGdip02_Art27")  
  
## <a name="using-regions"></a>使用区域  
 区域通常用于剪辑和命中测试。 剪辑涉及到将绘制限制到特定的区域的显示区域中，通常需要更新的部分。 命中测试涉及到检查以确定光标是否在某些区域中的屏幕时按下鼠标按钮。  
  
 您可以构造从一个矩形或路径的区域。 此外可以通过合并现有的区域来创建复杂的区域。 <xref:System.Drawing.Region>类提供了以下用于组合区域的方法： <xref:System.Drawing.Region.Intersect%2A>， <xref:System.Drawing.Region.Union%2A>， <xref:System.Drawing.Region.Xor%2A>， <xref:System.Drawing.Region.Exclude%2A>，并<xref:System.Drawing.Region.Complement%2A>。  
  
 两个区域的交集是属于这两个区域的所有点的集合。 联合是属于一个或另一个或两个区域中的所有点的集合。 区域的补数是不在区域中的所有点的集合。 下图显示了上图中所示的两个区域的并集和相交处。  
  
 ![Regions](./media/aboutgdip02-art28.gif "AboutGdip02_Art28")  
  
 <xref:System.Drawing.Region.Xor%2A>方法，适用于一对区域，会生成包含对一个区域或另一个，但不是能同时属于的所有点的区域。 <xref:System.Drawing.Region.Exclude%2A>方法，适用于一对区域，会生成包含不在第二个区域中的第一个区域中的所有点的区域。 下图显示了通过应用生成的区域<xref:System.Drawing.Region.Xor%2A>和<xref:System.Drawing.Region.Exclude%2A>本主题开头所示的两个区域的方法。  
  
 ![Regions](./media/aboutgdip02-art29.gif "AboutGdip02_Art29")  
  
 若要填充一个区域，需要<xref:System.Drawing.Graphics>对象，<xref:System.Drawing.Brush>对象，和一个<xref:System.Drawing.Region>对象。 <xref:System.Drawing.Graphics>对象提供<xref:System.Drawing.Graphics.FillRegion%2A>方法，和<xref:System.Drawing.Brush>对象将存储的填充，如颜色或图案的特性。 下面的示例填充用一种颜色的区域。  
  
 [!code-csharp[LinesCurvesAndShapes#61](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#61)]
 [!code-vb[LinesCurvesAndShapes#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [直线、曲线和图形](lines-curves-and-shapes.md)
- [使用区域](using-regions.md)
