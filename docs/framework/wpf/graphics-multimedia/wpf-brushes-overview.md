---
title: WPF 画笔概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 14e3d095d50f41e5b20a79d76c464bcf28c99327
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132205"
---
# <a name="wpf-brushes-overview"></a>WPF 画笔概述
在屏幕上可见的所有内容是可见的因为它通过画笔绘制。 例如，画笔用于描述背景的按钮、 文本、 前的景色和形状的填充。 本主题介绍的概念与绘制[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]画笔，并提供示例。 借助画笔，可以利用任意内容（从简单的纯色到复杂的图案和图像集）绘制 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 对象。  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a>使用画笔进行绘制  
 一个<xref:System.Windows.Media.Brush>"绘制"其输出区域。 不同画笔具有不同类型的输出。 某些画笔绘制用纯色，其他人使用渐变、 模式、 图像或绘图区域。 下图显示了每个不同的示例<xref:System.Windows.Media.Brush>类型。  
  
 ![画笔类型](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")  
画笔示例  
  
 大多数的视觉对象，可以指定绘制方式。 下表列出了一些常见对象和属性可以使用<xref:System.Windows.Media.Brush>。  
  
|类|画笔属性|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A>|  
|<xref:System.Windows.Controls.Control>|<xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 以下各节介绍了不同<xref:System.Windows.Media.Brush>类型，并提供每个示例。  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a>使用纯色进行绘制  
 一个<xref:System.Windows.Media.SolidColorBrush>使用纯色绘制区域<xref:System.Windows.Media.Color>。 有多种方式来指定<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>： 例如，您可以指定其 alpha、 红色、 蓝色和绿色通道或使用提供的预定义的颜色之一<xref:System.Windows.Media.Colors>类。  
  
 下面的示例使用<xref:System.Windows.Media.SolidColorBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下图显示绘制的矩形。  
  
 ![使用 SolidColorBrush 绘制的矩形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")  
使用 SolidColorBrush 绘制的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 有关详细信息<xref:System.Windows.Media.SolidColorBrush>类，请参阅[使用纯色和渐变概述进行绘制](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a>使用线性渐变进行绘制  
 一个<xref:System.Windows.Media.LinearGradientBrush>绘制带有线性渐变的区域。 线性渐变混合行，渐变轴跨两个或多个颜色。 您使用<xref:System.Windows.Media.GradientStop>对象渐变和它们的位置中指定的颜色。  
  
 下面的示例使用<xref:System.Windows.Media.LinearGradientBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下图显示绘制的矩形。  
  
 ![使用 LinearGradientBrush 绘制的矩形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")  
使用 LinearGradientBrush 绘制的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 有关详细信息<xref:System.Windows.Media.LinearGradientBrush>类，请参阅[使用纯色和渐变概述进行绘制](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a>使用径向渐变进行绘制  
 一个<xref:System.Windows.Media.RadialGradientBrush>使用径向渐变绘制区域。 径向渐变混合跨一个圆圈的两个或多个颜色。 如同<xref:System.Windows.Media.LinearGradientBrush>类，使用<xref:System.Windows.Media.GradientStop>对象渐变和它们的位置中指定的颜色。  
  
 下面的示例使用<xref:System.Windows.Media.RadialGradientBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下图显示绘制的矩形。  
  
 ![使用 RadialGradientBrush 绘制的矩形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")  
使用 RadialGradientBrush 绘制的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 有关详细信息<xref:System.Windows.Media.RadialGradientBrush>类，请参阅[使用纯色和渐变概述进行绘制](painting-with-solid-colors-and-gradients-overview.md)。  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a>使用图像进行绘制  
 <xref:System.Windows.Media.ImageBrush>使用绘制区域<xref:System.Windows.Media.ImageSource>。  
  
 下面的示例使用<xref:System.Windows.Media.ImageBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下图显示绘制的矩形。  
  
 ![使用 imagebrush 绘制的矩形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")  
使用图像绘制的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 有关详细信息<xref:System.Windows.Media.ImageBrush>类，请参阅[使用图像、 绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a>使用绘图进行绘制  
 一个<xref:System.Windows.Media.DrawingBrush>使用绘制区域<xref:System.Windows.Media.Drawing>。 一个<xref:System.Windows.Media.Drawing>可以包含形状、 图像、 文本和媒体。  
  
 下面的示例使用<xref:System.Windows.Media.DrawingBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下图显示绘制的矩形。  
  
 ![使用 DrawingBrush 绘制的矩形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")  
使用 DrawingBrush 绘制的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 有关详细信息<xref:System.Windows.Media.DrawingBrush>类，请参阅[使用图像、 绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a>使用视觉对象进行绘制  
 一个<xref:System.Windows.Media.VisualBrush>使用绘制区域<xref:System.Windows.Media.Visual>对象。 视觉对象的示例包括<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Page>，和<xref:System.Windows.Controls.MediaElement>。 一个<xref:System.Windows.Media.VisualBrush>，还可以将内容从一部分到另一个区域，则应用程序是用于创建反射效果和放大屏幕的部分非常有用。  
  
 下面的示例使用<xref:System.Windows.Media.VisualBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。 下图显示绘制的矩形。  
  
 ![使用 VisualBrush 绘制的矩形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")  
使用 VisualBrush 绘制的矩形  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 有关详细信息<xref:System.Windows.Media.VisualBrush>类，请参阅[使用图像、 绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a>使用预定义画笔和系统画笔进行绘制  
 为方便起见，Windows Presentation Foundation (WPF) 提供了一组预定义的系统画笔用于绘制对象。  
  
-   有关可用的预定义画笔的列表，请参阅<xref:System.Windows.Media.Brushes>类。 有关演示如何使用预定义的画笔的示例，请参阅[使用纯色绘制区域](how-to-paint-an-area-with-a-solid-color.md)。  
  
-   有关可用的系统画笔的列表，请参阅<xref:System.Windows.SystemColors>类。 有关示例，请参阅[使用系统画笔绘制区域](how-to-paint-an-area-with-a-system-brush.md)。  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a>常见的画笔功能  
 <xref:System.Windows.Media.Brush> 对象提供<xref:System.Windows.Media.Brush.Opacity%2A>属性，可用于使画笔显示为透明或部分透明。 <xref:System.Windows.Media.Brush.Opacity%2A>值为 0，则画笔完全透明，而<xref:System.Windows.Media.Brush.Opacity%2A>值为 1，则画笔完全不透明。 下面的示例使用<xref:System.Windows.Media.Brush.Opacity%2A>属性以使<xref:System.Windows.Media.SolidColorBrush>25%不透明。  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 如果画笔包含部分透明的颜色，颜色的不透明度值通过画笔的不透明度值相乘相结合。 例如，如果画笔的不透明度值 0.5 和画笔中使用的颜色还具有 0.5 的不透明度值，输出颜色具有 0.25 的不透明度值。  
  
> [!NOTE]
>  若要更改一个画笔的不透明度值更改整个元素使用的不透明度比效率更高其<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>属性。  
  
 可以旋转、 缩放、 倾斜和转换画笔的内容通过使用其<xref:System.Windows.Media.Brush.Transform%2A>或<xref:System.Windows.Media.Brush.RelativeTransform%2A>属性。 有关详细信息，请参阅[画笔转换概述](brush-transformation-overview.md)。  
  
 因为它们<xref:System.Windows.Media.Animation.Animatable>对象，<xref:System.Windows.Media.Brush>对象可进行动画处理。 有关详细信息，请参阅 [动画概述](animation-overview.md)。  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a>Freezable 功能  
 因为它继承自<xref:System.Windows.Freezable>类，<xref:System.Windows.Media.Brush>类提供多种特殊功能：<xref:System.Windows.Media.Brush>对象可声明为[资源](../advanced/xaml-resources.md)、 在多个对象之间共享和克隆。 此外，所有<xref:System.Windows.Media.Brush>除类型<xref:System.Windows.Media.VisualBrush>可以变为只读以提高性能并变为线程安全。  
  
 有关所提供的不同功能的详细信息<xref:System.Windows.Freezable>对象，请参阅[Freezable 对象概述](../advanced/freezable-objects-overview.md)。  
  
 有关原因的详细信息<xref:System.Windows.Media.VisualBrush>对象不能为冻结，请参阅<xref:System.Windows.Media.VisualBrush>类型页。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [使用纯色和渐变进行绘制概述](painting-with-solid-colors-and-gradients-overview.md)
- [使用图像、图形和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)
- [Freezable 对象概述](../advanced/freezable-objects-overview.md)
- [画笔示例](https://go.microsoft.com/fwlink/?LinkID=159973)
- [ImageBrush 示例](https://go.microsoft.com/fwlink/?LinkID=160005)
- [VisualBrush 示例](https://go.microsoft.com/fwlink/?LinkID=160049)
- [帮助主题](brushes-how-to-topics.md)
- [其他性能建议](../advanced/optimizing-performance-other-recommendations.md)
