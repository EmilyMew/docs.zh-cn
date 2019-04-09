---
title: 如何：创建二次贝塞尔曲线
ms.date: 03/30/2017
helpviewer_keywords:
- Bezier curves [WPF], creating
- quadratic Bezier curves [WPF], creating
- graphics [WPF], quadratic Bezier curves
ms.assetid: cd8fca4a-504e-4fd8-92ea-2969065a6e02
ms.openlocfilehash: a0b2145b4a5bba11186419fe680f2eca41949d6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134856"
---
# <a name="how-to-create-a-quadratic-bezier-curve"></a>如何：创建二次贝塞尔曲线
此示例演示如何创建二次贝塞尔曲线。  若要创建二次贝塞尔曲线，使用<xref:System.Windows.Media.PathGeometry>， <xref:System.Windows.Media.PathFigure>，和<xref:System.Windows.Media.QuadraticBezierSegment>类。  
  
## <a name="example"></a>示例  
 在以下示例中，从 (10100) 到 (300100) 绘制二次贝塞尔曲线。 该曲线的控制点为 (200200)。  
  
 [xaml]  
  
 在[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，可以使用特性语法来描述路径。  
  
 [!code-xaml[GeometrySample#54](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#54)]  
  
 [xaml]  
  
 (请注意，此属性语法实际上创建了<xref:System.Windows.Media.StreamGeometry>的轻量版本<xref:System.Windows.Media.PathGeometry>。 有关详细信息，请参阅[路径标记语法](path-markup-syntax.md)页。）  
  
 在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，还可以绘制二次贝塞尔曲线使用对象元素语法。 以下内容等效于之前的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 示例。  
  
 [!code-xaml[GeometrySample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 此示例是更大示例的组成部分；有关完整示例，请参阅[几何图形示例](https://go.microsoft.com/fwlink/?LinkID=159989)。  
  
## <a name="see-also"></a>请参阅

- [创建椭圆弧](how-to-create-an-elliptical-arc.md)
- [创建三次方贝塞尔曲线](how-to-create-a-cubic-bezier-curve.md)
