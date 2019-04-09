---
title: 如何：创建三次方贝塞尔曲线
ms.date: 03/30/2017
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
ms.openlocfilehash: 36544abc774b7fe82c2ff47483cfedd6fb13e344
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115565"
---
# <a name="how-to-create-a-cubic-bezier-curve"></a>如何：创建三次方贝塞尔曲线
此示例演示如何创建三次方贝塞尔曲线。 若要创建三次方贝塞尔曲线，使用<xref:System.Windows.Media.PathGeometry>， <xref:System.Windows.Media.PathFigure>，和<xref:System.Windows.Media.BezierSegment>类。  若要显示所生成的几何图形，请使用<xref:System.Windows.Shapes.Path>元素，或将其用于<xref:System.Windows.Media.GeometryDrawing>或<xref:System.Windows.Media.DrawingContext>。 在以下示例中，三次方贝塞尔曲线绘制从 （10，100） 到 （300，100）。 曲线的控制点为 （100，0） 和 （200，200）。  
  
## <a name="example"></a>示例  
 [xaml]  
  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，可以使用缩写的标记语法来描述路径。  
  
 [!code-xaml[GeometrySample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 [xaml]  
  
 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，还可以绘制使用对象标记的三次方贝塞尔曲线。 以下内容等效于之前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 示例。  
  
 [!code-xaml[GeometrySample#33](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 此示例是更大示例的组成部分；有关完整示例，请参阅[几何图形示例](https://go.microsoft.com/fwlink/?LinkID=159989)。  
  
## <a name="see-also"></a>请参阅

- [创建椭圆弧](how-to-create-an-elliptical-arc.md)
- [在 PathGeometry 中创建 LineSegment](how-to-create-a-linesegment-in-a-pathgeometry.md)
- [创建三次方贝塞尔曲线](how-to-create-a-cubic-bezier-curve.md)
- [创建二次贝塞尔曲线](how-to-create-a-quadratic-bezier-curve.md)
