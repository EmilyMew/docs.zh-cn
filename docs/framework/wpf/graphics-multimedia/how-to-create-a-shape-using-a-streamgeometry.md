---
title: 如何：使用 StreamGeometry 创建形状
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
ms.openlocfilehash: fd191e4cfdfa33c144389d4871a9641e9c811ed3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108597"
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a>如何：使用 StreamGeometry 创建形状
<xref:System.Windows.Media.StreamGeometry> 是轻量替代<xref:System.Windows.Media.PathGeometry>对于创建几何形状。 使用<xref:System.Windows.Media.StreamGeometry>何时需要描述复杂几何，但不是希望支持数据绑定、 动画或修改的开销。 例如，由于其效率<xref:System.Windows.Media.StreamGeometry>类是描述装饰器的一个不错选择。  
  
## <a name="example"></a>示例  
 下面的示例使用特性语法创建一个三角形<xref:System.Windows.Media.StreamGeometry>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 有关详细信息<xref:System.Windows.Media.StreamGeometry>属性的语法，请参阅[路径标记语法](path-markup-syntax.md)页。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Media.StreamGeometry>若要在代码中定义一个三角形。 首先，该示例将创建<xref:System.Windows.Media.StreamGeometry>，然后获取<xref:System.Windows.Media.StreamGeometryContext>并使用它来描述三角形。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a>示例  
 下一个示例创建一个方法，使用<xref:System.Windows.Media.StreamGeometry>和<xref:System.Windows.Media.StreamGeometryContext>定义几何形状基于指定的参数。  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.StreamGeometryContext>
- [使用 PathGeometry 创建形状](how-to-create-a-shape-by-using-a-pathgeometry.md)
- [Geometry 概述](geometry-overview.md)
