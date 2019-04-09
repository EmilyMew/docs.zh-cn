---
title: 如何：创建 GeometryDrawing
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: f5cdcfdb68ad8030bcbd6c689f45a8baddd000e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179785"
---
# <a name="how-to-create-a-geometrydrawing"></a>如何：创建 GeometryDrawing
此示例演示如何创建和显示<xref:System.Windows.Media.GeometryDrawing>。 一个<xref:System.Windows.Media.GeometryDrawing>使您能够通过关联来创建具有填充和边框的形状<xref:System.Windows.Media.Pen>和一个<xref:System.Windows.Media.Brush>与<xref:System.Windows.Media.Geometry>。 <xref:System.Windows.Media.GeometryDrawing.Geometry%2A>描述形状的结构<xref:System.Windows.Media.GeometryDrawing.Brush%2A>描述形状的填充和<xref:System.Windows.Media.GeometryDrawing.Pen%2A>描述形状的轮廓。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Media.GeometryDrawing>来呈现形状。 由描述形状<xref:System.Windows.Media.GeometryGroup>和两个<xref:System.Windows.Media.EllipseGeometry>对象。 用来绘制形状内部<xref:System.Windows.Media.LinearGradientBrush>并使用绘制其轮廓<xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>。 <xref:System.Windows.Media.GeometryDrawing>使用显示<xref:System.Windows.Media.ImageDrawing>和<xref:System.Windows.Controls.Image>元素。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 下图显示了生成<xref:System.Windows.Media.GeometryDrawing>。  
  
 ![两个椭圆的 GeometryDrawing](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")  
  
 若要创建更复杂的图形，可以将多个图形对象组合到一个单个复合图形使用<xref:System.Windows.Media.DrawingGroup>。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.DrawingGroup>
- [Drawing 对象概述](drawing-objects-overview.md)
- [Geometry 概述](geometry-overview.md)
- [创建复合绘图](how-to-create-a-composite-drawing.md)
