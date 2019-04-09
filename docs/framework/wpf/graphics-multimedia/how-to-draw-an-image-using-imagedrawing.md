---
title: 如何：使用 ImageDrawing 绘制图像
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: f9459185bf81160b45222e7d6821e0f945ada381
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59100153"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>如何：使用 ImageDrawing 绘制图像
此示例演示如何使用<xref:System.Windows.Media.ImageDrawing>要绘制图像。 <xref:System.Windows.Media.ImageDrawing>允许您显示<xref:System.Windows.Media.ImageSource>与<xref:System.Windows.Media.DrawingBrush>， <xref:System.Windows.Media.DrawingImage>，或<xref:System.Windows.Media.Visual>。 若要绘制图像，则创建<xref:System.Windows.Media.ImageDrawing>并设置其<xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>和<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>属性。 <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>属性指定要绘制，图像和<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>属性指定的位置和每个图像的大小。  
  
## <a name="example"></a>示例  
 下面的示例创建复合绘图使用四个<xref:System.Windows.Media.ImageDrawing>对象。 此示例将生成以下映像：  
  
 ![几个 DrawingImage 对象](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
四个 ImageDrawing 对象  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 有关演示简单的方法来显示图像而不使用的示例<xref:System.Windows.Media.ImageDrawing>，请参阅[使用 Image 元素](../controls/how-to-use-the-image-element.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [Drawing 对象概述](drawing-objects-overview.md)
- [Freezable 对象概述](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze 特性](../advanced/presentationoptions-freeze-attribute.md)
