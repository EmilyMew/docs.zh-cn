---
title: 如何：使用纯色绘制区域
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: c85ba72c858d155f29875bb944824db1c44ffaab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086840"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>如何：使用纯色绘制区域
若要绘制使用纯色区域，可以使用预定义的系统画笔，如<xref:System.Windows.Media.Brushes.Red%2A>或<xref:System.Windows.Media.Brushes.Blue%2A>，也可以创建一个新<xref:System.Windows.Media.SolidColorBrush>并描述其<xref:System.Windows.Media.SolidColorBrush.Color%2A>使用 alpha、 红色、 绿色和蓝色值。 在 XAML 中，还可以使用十六进制表示法来利用纯色绘制区域。  
  
 下面的示例使用上述每种方法来绘制<xref:System.Windows.Shapes.Rectangle>蓝色。  
  
## <a name="example"></a>示例  
 **使用预定义的画笔**  
  
 在下面的示例使用预定义的画笔<xref:System.Windows.Media.Brushes.Blue%2A>来绘制一个蓝色矩形。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **使用十六进制表示法**  
  
 下一个示例使用 8 位十六进制表示法绘制一个蓝色矩形。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **使用 ARGB 值**  
  
 下一个示例创建<xref:System.Windows.Media.SolidColorBrush>并介绍了其<xref:System.Windows.Media.SolidColorBrush.Color%2A>使用 ARGB 值为蓝色。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 有关描述颜色的其他方法，请参阅<xref:System.Windows.Media.Color>结构。  
  
 **相关主题**  
  
 有关详细信息<xref:System.Windows.Media.SolidColorBrush>和其他示例，请参阅[使用纯色和渐变概述进行绘制](painting-with-solid-colors-and-gradients-overview.md)概述。  
  
 此代码示例是为提供一个更大示例的一部分<xref:System.Windows.Media.SolidColorBrush>类。 有关完整示例，请参阅[画笔示例](https://go.microsoft.com/fwlink/?LinkID=159973)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Brushes>
