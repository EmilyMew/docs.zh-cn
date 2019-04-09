---
title: 优化性能：二维图形和图像处理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], performance
- drawing [WPF], optimizing performance
- imaging [WPF], optimizing performance
- shapes [WPF], optimizing performance
- 2-D graphics [WPF]
- images [WPF], optimizing performance
ms.assetid: e335601e-28c8-4d64-ba27-778fffd55f72
ms.openlocfilehash: 4fca9231872a268470c9bcfa73e7a0c0a26d300c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074984"
---
# <a name="optimizing-performance-2d-graphics-and-imaging"></a>优化性能：二维图形和图像处理
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供各种二维图形和图像处理功能，可以优化你的应用程序要求。 本主题提供有关这些方面性能优化的信息。  

<a name="Drawing_and_Shapes"></a>   
## <a name="drawing-and-shapes"></a>绘图和形状  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了<xref:System.Windows.Media.Drawing>和<xref:System.Windows.Shapes.Shape>对象来表示图形绘制内容。 但是，<xref:System.Windows.Media.Drawing>对象是相比更为简单的构造<xref:System.Windows.Shapes.Shape>对象，并提供更好的性能特征。  
  
 一个<xref:System.Windows.Shapes.Shape>，可将图形形状绘制到屏幕。 因为派生自<xref:System.Windows.FrameworkElement>类，<xref:System.Windows.Shapes.Shape>对象可以用在面板和多数控件。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了图形和呈现服务的访问权限的多个层。 在顶层，<xref:System.Windows.Shapes.Shape>对象是易于使用和提供许多有用的功能，如布局和事件处理。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了随时可用形状对象数。 所有形状对象都继承自<xref:System.Windows.Shapes.Shape>类。 可用形状对象包括<xref:System.Windows.Shapes.Ellipse>， <xref:System.Windows.Shapes.Line>， <xref:System.Windows.Shapes.Path>， <xref:System.Windows.Shapes.Polygon>， <xref:System.Windows.Shapes.Polyline>，并<xref:System.Windows.Shapes.Rectangle>。  
  
 <xref:System.Windows.Media.Drawing> 对象，但是，并非派生<xref:System.Windows.FrameworkElement>类，并提供用于呈现形状、 图像和文本的轻量实现。  
  
 有四种类型的<xref:System.Windows.Media.Drawing>对象：  
  
-   <xref:System.Windows.Media.GeometryDrawing> 绘制形状。  
  
-   <xref:System.Windows.Media.ImageDrawing> 绘制图像。  
  
-   <xref:System.Windows.Media.GlyphRunDrawing> 绘制文本。  
  
-   <xref:System.Windows.Media.DrawingGroup> 绘制其他绘图。 使用图形组将其他图形合并到单个复合图形。  
  
 <xref:System.Windows.Media.GeometryDrawing>对象用于绘制几何内容。 <xref:System.Windows.Media.Geometry>类和具体类派生，如<xref:System.Windows.Media.CombinedGeometry>， <xref:System.Windows.Media.EllipseGeometry>，和<xref:System.Windows.Media.PathGeometry>、 用于呈现二维图形提供一种方式，以及提供命中测试和剪裁支持。 几何对象可用于定义控件的区域或定义应用于图像的剪裁区域等。 几何对象可以是简单区域（例如矩形和圆形），或者是由两个或多个几何对象创建的复合区域。 可以通过组合创建更复杂的几何区域<xref:System.Windows.Media.PathSegment>的派生的对象，如<xref:System.Windows.Media.ArcSegment>， <xref:System.Windows.Media.BezierSegment>，和<xref:System.Windows.Media.QuadraticBezierSegment>。  
  
 表面上看，<xref:System.Windows.Media.Geometry>类和<xref:System.Windows.Shapes.Shape>类是非常相似。 二者都用于绘制 2D 图形和都具有相似的具体类派生，例如，<xref:System.Windows.Media.EllipseGeometry>和<xref:System.Windows.Shapes.Ellipse>。 但是，这两个类集之间存在重大区别。 对于其中一个，<xref:System.Windows.Media.Geometry>类所缺少的功能的一些<xref:System.Windows.Shapes.Shape>类，例如绘制自身的功能。 若要绘制几何对象，必须使用另一个类（例如 DrawingContext、Drawing 或 Path（值得注意的是 Path 是一个 Shape））来执行绘制操作。 填充、笔划和笔划粗细等绘制属性位于绘制几何对象的类上，而形状对象中包含这些属性。 可以这样来理解这种差别：几何对象定义区域（例如圆形），而形状对象定义区域、定义如何填充区域和设置区域边框并参与布局系统。  
  
 由于<xref:System.Windows.Shapes.Shape>对象派生自<xref:System.Windows.FrameworkElement>类，使用它们可以在你的应用程序中添加内存消耗显著增加。 如果您确实不需要<xref:System.Windows.FrameworkElement>功能对于图形内容，请考虑使用轻量<xref:System.Windows.Media.Drawing>对象。  
  
 有关详细信息<xref:System.Windows.Media.Drawing>对象，请参阅[Drawing 对象概述](../graphics-multimedia/drawing-objects-overview.md)。  
  
<a name="StreamGeometry_Objects"></a>   
## <a name="streamgeometry-objects"></a>StreamGeometry 对象  
 <xref:System.Windows.Media.StreamGeometry>对象是的轻型替代方法<xref:System.Windows.Media.PathGeometry>对于创建几何形状。 使用<xref:System.Windows.Media.StreamGeometry>何时需要描述复杂几何。 <xref:System.Windows.Media.StreamGeometry> 用于处理多个优化<xref:System.Windows.Media.PathGeometry>对象，并执行更好地与使用多个独立相比<xref:System.Windows.Media.PathGeometry>对象。  
  
 下面的示例使用特性语法创建一个三角形<xref:System.Windows.Media.StreamGeometry>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 有关详细信息<xref:System.Windows.Media.StreamGeometry>对象，请参阅[形状使用 StreamGeometry 创建](../graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md)。  
  
<a name="DrawingVisual_Objects"></a>   
## <a name="drawingvisual-objects"></a>DrawingVisual 对象  
 <xref:System.Windows.Media.DrawingVisual>对象是一个轻量绘图类，用于呈现形状、 图像或文本。 此类之所以为轻量类是因为它不提供布局或事件处理，从而性能得以提升。 因此，绘图非常适用于背景和剪贴画。 有关详细信息，请参阅[使用 DrawingVisual 对象](../graphics-multimedia/using-drawingvisual-objects.md)。  
  
<a name="Images"></a>   
## <a name="images"></a>图像  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 映像在以前版本的中的图像处理功能可以显著地提高[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]。 显示位图或在公共控件上使用图像等图像处理功能以前主要由 Microsoft Windows 图形设备接口 (GDI) 或Microsoft Windows GDI+ 应用程序编程接口 (API) 处理。 这些 API 提供基线图像处理功能，但缺少编解码器扩展性支持和高保真图像支持等功能。 WPF 图像处理 API 已经过重新设计，克服了 GDI 和 GDI+ 的缺点，提供新的 API 集以在应用程序内显示和使用图像。  
  
 使用图像时，为使性能更佳，请考虑以下建议：  
  
-   如果应用程序要求显示缩略图，请考虑创建一个缩略版图像。 默认情况下，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 会加载图像并将其解码到最大尺寸。 如果仅需要缩略版本图像，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 会先将图像解码为完整尺寸，然后将其缩放为缩略图大小，这个过程是多余的。 若要避免此多余的过程，可请求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 将图像解码到缩略图大小，或者请求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 加载缩略图大小的图像。  
  
-   请务必将图像解码到所需大小而不是默认大小。 如上所述，请求 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 将图像解码为所需大小而不是默认的最大尺寸。 这样不仅会减小应用程序的工作集，还会减慢其执行速度。  
  
-   如果可能，请将多个图像合并到单个图像中，例如由多个图像构成的胶卷条。  
  
-   有关详细信息，请参阅 [图像概述](../graphics-multimedia/imaging-overview.md)。  
  
### <a name="bitmapscalingmode"></a>BitmapScalingMode  
 对任何位图缩放进行动画处理时，默认高质量图像重采样算法有时可能由于消耗过多系统资源导致帧速率下降，从而导致动画明显变慢。 通过设置<xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>的属性<xref:System.Windows.Media.RenderOptions>对象传递给<xref:System.Windows.Media.BitmapScalingMode.LowQuality>缩放位图时，可以创建更为流畅的动画。 <xref:System.Windows.Media.BitmapScalingMode.LowQuality> 模式告知[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]呈现引擎处理图像时从质量优化算法切换到速度优化算法。  
  
 下面的示例演示如何设置<xref:System.Windows.Media.BitmapScalingMode>图像对象。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet2)]
 [!code-vb[RenderOptions#RenderOptionsSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet2)]  
  
### <a name="cachinghint"></a>CachingHint  
 默认情况下[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]不会缓存的已呈现的内容<xref:System.Windows.Media.TileBrush>对象，如<xref:System.Windows.Media.DrawingBrush>和<xref:System.Windows.Media.VisualBrush>。 在静态方案中的内容和使用都不<xref:System.Windows.Media.TileBrush>中更改场景中，这是有意义，因为这可节省视频内存。 如得意义时不会使<xref:System.Windows.Media.TileBrush>中的非静态方法使用具有静态内容-例如，当一个静态<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>映射到旋转 3D 对象的图面。 默认行为[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]重新呈现内容的整个<xref:System.Windows.Media.DrawingBrush>或<xref:System.Windows.Media.VisualBrush>对于每个框架，即使内容是不变。  
  
 通过设置<xref:System.Windows.Media.RenderOptions.CachingHint%2A>的属性<xref:System.Windows.Media.RenderOptions>对象传递给<xref:System.Windows.Media.CachingHint.Cache>可以通过使用缓存的版平铺的画笔对象提高性能。  
  
 <xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMinimum%2A>并<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>属性值是相对大小值，确定何时<xref:System.Windows.Media.TileBrush>应更改而重新生成对象。 例如，通过设置<xref:System.Windows.Media.RenderOptions.CacheInvalidationThresholdMaximum%2A>属性设置为 2.0 中，为缓存<xref:System.Windows.Media.TileBrush>仅需要其大小超过当前缓存的大小的两倍时重新生成。  
  
 下面的示例演示如何使用缓存提示选项用于<xref:System.Windows.Media.DrawingBrush>。  
  
 [!code-csharp[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/RenderOptions/CSharp/Window1.xaml.cs#renderoptionssnippet3)]
 [!code-vb[RenderOptions#RenderOptionsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RenderOptions/visualbasic/window1.xaml.vb#renderoptionssnippet3)]  
  
## <a name="see-also"></a>请参阅

- [优化 WPF 应用程序性能](optimizing-wpf-application-performance.md)
- [规划应用程序性能](planning-for-application-performance.md)
- [利用硬件](optimizing-performance-taking-advantage-of-hardware.md)
- [布局和示例](optimizing-performance-layout-and-design.md)
- [对象行为](optimizing-performance-object-behavior.md)
- [应用程序资源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [数据绑定](optimizing-performance-data-binding.md)
- [其他性能建议](optimizing-performance-other-recommendations.md)
- [动画提示和技巧](../graphics-multimedia/animation-tips-and-tricks.md)
