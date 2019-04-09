---
title: 如何：使用 RectangleGeometry 定义矩形
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 146ca7017ee38ad5c1065e59662ac441e7bfbfe2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075791"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>如何：使用 RectangleGeometry 定义矩形
此示例介绍了如何使用<xref:System.Windows.Media.RectangleGeometry>类，用于描述一个矩形。  
  
## <a name="example"></a>示例  
 下面的示例演示如何创建和呈现<xref:System.Windows.Media.RectangleGeometry>。  通过定义相对位置和矩形的尺寸<xref:System.Windows.Rect>结构。 相对位置是`50,50`和高度和宽度均`25`创建一个正方形。 与绘制矩形的内部<xref:System.Windows.Media.Brushes.LemonChiffon%2A>用来绘制画笔，它的轮廓<xref:System.Windows.Media.Brushes.Black%2A>笔画粗细为`1`。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![一个 RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 虽然此示例使用了<xref:System.Windows.Shapes.Path>元素来呈现<xref:System.Windows.Media.RectangleGeometry>，有许多其他方法来使用<xref:System.Windows.Media.RectangleGeometry>对象。 例如，<xref:System.Windows.Media.RectangleGeometry>可用于指定<xref:System.Windows.UIElement.Clip%2A>的<xref:System.Windows.UIElement>或<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>的<xref:System.Windows.Media.GeometryDrawing>。  
  
 其他简单的几何类包括<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.EllipseGeometry>。 这些几何形状，以及更复杂的也可以创建使用<xref:System.Windows.Media.PathGeometry>或<xref:System.Windows.Media.StreamGeometry>。  
  
## <a name="see-also"></a>请参阅

- [Geometry 概述](geometry-overview.md)
- [创建复合形状](how-to-create-a-composite-shape.md)
- [使用 PathGeometry 创建形状](how-to-create-a-shape-by-using-a-pathgeometry.md)
