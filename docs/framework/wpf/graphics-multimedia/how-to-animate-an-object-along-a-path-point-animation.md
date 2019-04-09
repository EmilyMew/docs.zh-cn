---
title: 如何：沿着路径针对对象进行动画处理（点动画）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: 4ef28118975d02500916676ca50e0f9622c7a3e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129579"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>如何：沿着路径针对对象进行动画处理（点动画）
此示例演示如何使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>对象进行动画处理<xref:System.Windows.Point>沿着曲线路径。  
  
## <a name="example"></a>示例  
 以下示例将移动<xref:System.Windows.Media.EllipseGeometry>沿着由定义路径<xref:System.Windows.Media.PathGeometry>。 椭圆几何图形<xref:System.Windows.Media.EllipseGeometry.Center%2A>属性，采用<xref:System.Windows.Point>值，指定其位置; 若要移动椭圆几何图形，您进行动画处理其<xref:System.Windows.Media.EllipseGeometry.Center%2A>属性。 该示例使用<xref:System.Windows.Media.Animation.PointAnimationUsingPath>进行动画处理<xref:System.Windows.Media.EllipseGeometry>对象的<xref:System.Windows.Media.EllipseGeometry.Center%2A>属性。  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 有关完整示例，请参阅[路径动画示例](https://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 使用前面示例的代码版本<xref:System.Windows.Media.Animation.Storyboard>进行动画处理<xref:System.Windows.Media.EllipseGeometry>，即使只有一个动画已应用。 一个<xref:System.Windows.Media.Animation.Storyboard>通常是因为这些动画可以控制由同一个应用多个动画的最简单方式<xref:System.Windows.Media.Animation.Storyboard>。 但是，使用代码时，将一个动画应用到属性的更简单方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。 有关示例，请参阅[在不使用情节提要的情况下对属性进行动画处理](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>请参阅

- [路径动画示例](https://go.microsoft.com/fwlink/?LinkID=160028)
- [动画概述](animation-overview.md)
- [路径动画帮助主题](path-animation-how-to-topics.md)
