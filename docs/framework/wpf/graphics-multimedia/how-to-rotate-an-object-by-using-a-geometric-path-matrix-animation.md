---
title: 如何：使用几何路径旋转对象（矩阵动画）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 8f1b0ac42ea7509f8bc22b0bd2f50e2f96b5bee5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087880"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a>如何：使用几何路径旋转对象（矩阵动画）
此示例演示如何使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>和一个<xref:System.Windows.Media.MatrixTransform>旋转 （转动） 某个对象沿几何路径由定义<xref:System.Windows.Media.PathGeometry>对象。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath>对象进行动画处理<xref:System.Windows.Media.MatrixTransform.Matrix%2A>属性的<xref:System.Windows.Media.MatrixTransform>。 <xref:System.Windows.Media.MatrixTransform>应用于按钮，并使其沿着曲线路径移动。 因为<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A>属性设置为`true`，矩形将沿着路径的切线旋转。  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 有关完整示例，请参阅[路径动画示例](https://go.microsoft.com/fwlink/?LinkID=160028)。  
  
 使用前面示例的代码版本<xref:System.Windows.Media.Animation.Storyboard>进行动画处理<xref:System.Windows.Media.EllipseGeometry>，即使只有一个动画已应用。 将一个动画应用到代码中的属性的更简单方法是使用<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法。 有关示例，请参阅[在不使用情节提要的情况下对属性进行动画处理](how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>请参阅

- [动画概述](animation-overview.md)
- [路径动画帮助主题](path-animation-how-to-topics.md)
- [路径动画示例](https://go.microsoft.com/fwlink/?LinkID=160028)
