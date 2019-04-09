---
title: 如何：圆化 RectangleGeometry 的角
ms.date: 03/30/2017
helpviewer_keywords:
- corners [WPF], rounding
- RectangleGeometry class [WPF], rounding corners
- graphics [WPF], rounding corners of RectangleGeometry objects [WPF]
- rounding corners of RectangleGeometry objects [WPF]
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
ms.openlocfilehash: eb2f173bedb903e12b2795264c684524cfa09825
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089128"
---
# <a name="how-to-round-the-corners-of-a-rectanglegeometry"></a>如何：圆化 RectangleGeometry 的角
要舍入的边角<xref:System.Windows.Media.RectangleGeometry>，请将其<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>属性设置为大于零的值。 值越大，1 之间的矩形的角。  
  
## <a name="example"></a>示例  
 下面的示例显示了一些<xref:System.Windows.Media.RectangleGeometry>具有不同的对象<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A>和<xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>设置。 <xref:System.Windows.Media.RectangleGeometry>对象会显示使用<xref:System.Windows.Shapes.Path>元素。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![使用不同的 RadiusX 矩形&#47;RadiusY 设置](./media/graphicsmm-rounded.png "graphicsmm_rounded")  
圆角矩形  
  
## <a name="see-also"></a>请参阅

- [Geometry 概述](geometry-overview.md)
- [创建复合形状](how-to-create-a-composite-shape.md)
- [使用 PathGeometry 创建形状](how-to-create-a-shape-by-using-a-pathgeometry.md)
