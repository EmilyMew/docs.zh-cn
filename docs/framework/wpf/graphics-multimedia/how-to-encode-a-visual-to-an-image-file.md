---
title: 如何：将 Visual 编码为图像文件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 872c19af0cfcf4fc980643c37e9a6028457c03b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096779"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>如何：将 Visual 编码为图像文件
此示例演示如何进行编码<xref:System.Windows.Media.Visual>为图像文件，并使用对象<xref:System.Windows.Media.Imaging.RenderTargetBitmap>和一个<xref:System.Windows.Media.Imaging.PngBitmapEncoder>。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Media.DrawingVisual>使用创建<xref:System.Windows.Media.Imaging.BitmapImage>并<xref:System.Windows.Media.FormattedText>呈现到<xref:System.Windows.Media.Imaging.RenderTargetBitmap>。 呈现的位图随后用于创建<xref:System.Windows.Media.Imaging.BitmapFrame>添加到<xref:System.Windows.Media.Imaging.PngBitmapEncoder>若要创建一个新[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]文件。  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 一个<xref:System.Windows.Media.Imaging.PngBitmapEncoder>使用在此示例中，但任何派生<xref:System.Windows.Media.Imaging.BitmapEncoder>对象可能已用来创建图像文件。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.DrawingContext>
- [图像处理概述](imaging-overview.md)
- [Drawing 对象概述](drawing-objects-overview.md)
- [使用 DrawingVisual 对象](using-drawingvisual-objects.md)
