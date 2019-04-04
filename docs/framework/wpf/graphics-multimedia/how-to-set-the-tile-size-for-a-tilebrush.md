---
title: 如何：设置 TileBrush 的平铺大小
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 80b5dfc668464df829db593668bea8a9a4ec09e4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839670"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>如何：设置 TileBrush 的平铺大小

此示例演示如何设置平铺大小<xref:System.Windows.Media.TileBrush>。 默认情况下，<xref:System.Windows.Media.TileBrush>生成完全填充要绘制区域的单个磁贴。 可以通过设置替代此行为<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>属性。

<xref:System.Windows.Media.TileBrush.Viewport%2A>属性指定的磁贴大小<xref:System.Windows.Media.TileBrush>。 默认情况下的值<xref:System.Windows.Media.TileBrush.Viewport%2A>属性是相对于所绘制的区域的大小。 若要使<xref:System.Windows.Media.TileBrush.Viewport%2A>属性指定绝对平铺大小，设置<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>属性设置为<xref:System.Windows.Media.BrushMappingMode.Absolute>。

## <a name="example"></a>示例

下面的示例使用<xref:System.Windows.Media.ImageBrush>，一种类型的<xref:System.Windows.Media.TileBrush>、 绘制一个矩形与磁贴。 该示例设置为 50%的输出区域 （矩形） 的 50%的每个磁贴。 因此，将用四个投影图像绘制该矩形。

下图显示了该示例生成的输出：

![一个具有四个樱桃演示使用图像画笔平铺的矩形。](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

下一个示例创建<xref:System.Windows.Media.ImageBrush>，设置其<xref:System.Windows.Media.TileBrush.Viewport%2A>到`0,0,25,25`并将其<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>到<xref:System.Windows.Media.BrushMappingMode.Absolute>，并使用它来绘制另一个矩形。 因此，画笔会生成一个宽度为 25 像素、高度为 25 像素的平铺。

下图显示了该示例生成的输出：

![一个具有 40 八樱桃演示的平铺的 TileBrush 的视区的矩形。](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

以上几个示例摘自一个更大的示例。 有关完整示例，请参阅[ImageBrush 示例](https://go.microsoft.com/fwlink/?LinkID=160005)。

虽然此示例使用<xref:System.Windows.Media.ImageBrush>类，<xref:System.Windows.Media.TileBrush.Viewport%2A>和<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>属性的行为方式相同其他<xref:System.Windows.Media.TileBrush>对象，即，对于<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。 有关详细信息<xref:System.Windows.Media.ImageBrush>和其他<xref:System.Windows.Media.TileBrush>对象，请参阅[使用图像、 绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.TileBrush>
- [使用图像、绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)
- [使用 TileBrush 创建不同的平铺图案](how-to-create-different-tile-patterns-with-a-tilebrush.md)
