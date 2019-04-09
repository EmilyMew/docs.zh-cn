---
title: 如何：创建复合绘图
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], composite
- composite drawings [WPF]
- graphics [WPF], composite drawings
ms.assetid: 066eb0ab-5f0e-439d-85c6-dca60af269fc
ms.openlocfilehash: 0af7fbca593627ebe8cd102a02617a27eac50aa5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132465"
---
# <a name="how-to-create-a-composite-drawing"></a>如何：创建复合绘图
此示例演示如何使用<xref:System.Windows.Media.DrawingGroup>若要通过组合多个创建复杂的图形<xref:System.Windows.Media.Drawing>为单个复合绘图的对象。  
  
## <a name="example"></a>示例  
 下面的示例使用<xref:System.Windows.Media.DrawingGroup>以创建从绘制组合<xref:System.Windows.Media.GeometryDrawing>和<xref:System.Windows.Media.ImageDrawing>对象。 下图显示了此示例生成的输出。  
  
 ![具有多个绘图的 DrawingGroup](./media/graphicsmm-simple.jpg "graphicsmm_simple")  
通过使用 DrawingGroup 创建复合绘图  
  
 请注意显示的绘制边界的灰色边框。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmsimpledrawinggroupexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMSimpleDrawingGroupExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmsimpledrawinggroupexample)]  
  
 可以使用<xref:System.Windows.Media.DrawingGroup>以应用<xref:System.Windows.Media.DrawingGroup.Transform%2A>，<xref:System.Windows.Media.DrawingGroup.Opacity%2A>设置，请<xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>， <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>， <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>，或<xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>于它包含的绘图。 因为<xref:System.Windows.Media.DrawingGroup>也是<xref:System.Windows.Media.Drawing>，它可以包含其他<xref:System.Windows.Media.DrawingGroup>对象。  
  
 下面的示例是类似于前面的示例，只不过它使用其他<xref:System.Windows.Media.DrawingGroup>要应用于某些图形的位图效果和不透明蒙板的对象。 下图显示了此示例生成的输出。  
  
 ![具有多个绘图的 DrawingGroup](./media/graphicsmm-multiple.jpg "graphicsmm_multiple")  
复合图形的具有多个 DrawingGroup 对象  
  
 请注意显示的绘制边界的灰色边框。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupExample.cs#graphicsmmmultipledrawinggroupsexample)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMMultipleDrawingGroupsExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupExample.xaml#graphicsmmmultipledrawinggroupsexample)]  
  
 有关详细信息<xref:System.Windows.Media.Drawing>对象，请参阅[Drawing 对象概述](drawing-objects-overview.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>
- <xref:System.Windows.Media.DrawingGroup.Transform%2A>
- <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>
- <xref:System.Windows.Media.DrawingGroup.Opacity%2A>
- <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>
- <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>
- [Drawing 对象概述](drawing-objects-overview.md)
