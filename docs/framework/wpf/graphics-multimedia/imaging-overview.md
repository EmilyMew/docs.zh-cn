---
title: 图像处理概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
ms.openlocfilehash: 45214b5f0e6827c36f87a4d45592ff0989c9a877
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890805"
---
# <a name="imaging-overview"></a>图像处理概述
本主题介绍 [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 开发人员可以显示、 转换和设置图像的格式。  
  
  
<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>WPF 图像处理组件  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 提供的图像处理功能的重大改进[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]。 以前，图像处理功能（例如在公共控件上显示位图或使用图像）依赖于 [!INCLUDE[TLA#tla_gdi](../../../../includes/tlasharptla-gdi-md.md)] 或 [!INCLUDE[TLA#tla_gdiplus](../../../../includes/tlasharptla-gdiplus-md.md)] 库。 这些 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 提供了基线图像处理功能，但缺乏诸如编解码器扩展性支持和高保真图像支持之类的功能。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 旨在克服的不足之处[!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]并[!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)]，并提供一组新的[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]以显示和使用你的应用程序中的图像。  
  
 有两种方式可以访问 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]：托管组件和非托管组件。 非托管组件提供以下功能。  
  
-   适用于新的或专用图像格式的扩展性模型。  
  
-   对包括 [!INCLUDE[TLA#tla_bmp](../../../../includes/tlasharptla-bmp-md.md)]、[!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)]、[!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]、[!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)]、[!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)]、[!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] 和图标 (.ico) 在内的本机图像格式增强了性能和安全性。  
  
-   高位深图像数据最多保留 8 位/通道（32 位/像素）。  
  
-   非破坏性图像缩放、剪切和旋转。  
  
-   简化的颜色管理。  
  
-   对文件内的专用元数据的支持。  
  
-   托管组件利用非托管基础结构提供图像与其他 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 功能（如 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、动画和图形）的无缝集成。 托管的组件还可以利用 Windows Presentation Foundation (WPF) 图像处理编解码器扩展性模型可以自动识别中的新图像格式的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]应用程序。  
  
 大多数托管[!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)][!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]驻留在<xref:System.Windows.Media.Imaging?displayProperty=nameWithType>命名空间，但一些重要类型，如<xref:System.Windows.Media.ImageBrush>并<xref:System.Windows.Media.ImageDrawing>驻留在<xref:System.Windows.Media?displayProperty=nameWithType>命名空间和<xref:System.Windows.Controls.Image>驻留在<xref:System.Windows.Controls?displayProperty=nameWithType>命名空间。  
  
 本主题提供有关托管组件的其他信息。 有关非托管 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 的详细信息，请参阅[非托管 WPF 图像处理组件](/windows/desktop/wic/-wic-lh)文档。  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>WPF 图像格式  
 编解码器用于对特定媒体格式进行解码或编码。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 包括适用于编解码器[!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)]， [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]， [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]， [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]， [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)]， [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]，和 ICON 图像格式。 利用上述每个编解码器，应用程序可以对其各自的图像格式进行解码（ICON 除外）和编码。  
  
 <xref:System.Windows.Media.Imaging.BitmapSource> 一个重要的类用于解码和编码的图像。 它是 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 管道的基本构建基块，表示具有特定大小和分辨率的单个不变的像素集。 一个<xref:System.Windows.Media.Imaging.BitmapSource>可以是单个帧的多个帧图像，也可以是上执行转换的结果<xref:System.Windows.Media.Imaging.BitmapSource>。 它是许多中使用的主类的父级[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]如映像<xref:System.Windows.Media.Imaging.BitmapFrame>。  
  
 一个<xref:System.Windows.Media.Imaging.BitmapFrame>用于存储的图像格式的实际位图数据。 许多图像格式仅支持一个<xref:System.Windows.Media.Imaging.BitmapFrame>，尽管等格式[!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)]和[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]支持每个图像的多个帧。 帧由解码器用作输入数据，并传递到编码器以创建图像文件。  
  
 下面的示例演示如何<xref:System.Windows.Media.Imaging.BitmapFrame>创建从<xref:System.Windows.Media.Imaging.BitmapSource>，然后添加到[!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)]映像。  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>图像格式解码  
 图像解码是指将某种图像格式转换为可以由系统使用的图像数据。 然后，此图像数据可以用于显示、处理或编码为其他格式。 根据图像格式选择解码器。 自动选择编解码器，除非指定了特定解码器。 [在 WPF 中显示图像](#_displayingimages)一节中的示例演示了自动解码。 使用非托管 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 界面开发并向系统注册的自定义格式解码器会自动加入到解码器选择队列。 这将使得自定义格式可以自动显示在 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 应用程序中。  
  
 以下示例演示使用位图解码器对 [!INCLUDE[TLA2#tla_bmp](../../../../includes/tla2sharptla-bmp-md.md)] 格式图像进行解码。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>图像格式编码  
 图像编码是指将图像数据转换为特定的图像格式。 然后，已编码的图像数据可以用于创建新的图像文件。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 为每个前面所述的图像格式提供编码器。  
  
 以下示例演示使用编码器保存一个新创建的位图图像。  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>在 WPF 中显示图像  
 有几种方法可在 Windows Presentation Foundation (WPF) 应用程序中显示图像。 可以使用显示图像<xref:System.Windows.Controls.Image>控件，visual 使用绘制<xref:System.Windows.Media.ImageBrush>，或使用绘制<xref:System.Windows.Media.ImageDrawing>。  
  
### <a name="using-the-image-control"></a>使用 Image 控件  
 <xref:System.Windows.Controls.Image> 是一个框架元素，在应用程序中显示图像的主要方法。 在中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，<xref:System.Windows.Controls.Image>可以采用两种方法; 特性语法或属性语法。 以下示例演示如何使用特性语法或属性标记语法来呈现宽度为 200 像素的图像。 有关特性语法和属性语法的详细信息，请参阅[依赖属性概述](../advanced/dependency-properties-overview.md)。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 许多示例使用<xref:System.Windows.Media.Imaging.BitmapImage>对象，以引用的图像文件。 <xref:System.Windows.Media.Imaging.BitmapImage> 是一个专用<xref:System.Windows.Media.Imaging.BitmapSource>适用于[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]加载和是显示为图像的简单办法<xref:System.Windows.Controls.Image.Source%2A>的<xref:System.Windows.Controls.Image>控件。  
  
 以下示例演示如何使用代码呈现宽度为 200 像素的图像。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage> 实现<xref:System.ComponentModel.ISupportInitialize>接口来优化对多个属性的初始化。 只能在对象初始化过程中进行属性更改。 调用<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>发出信号的初始化已开始和<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>发出信号的初始化已完成。 初始化后，将忽略所做的属性更改。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>旋转、转换和剪切图像  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 使用户能够使用的属性转换图像<xref:System.Windows.Media.Imaging.BitmapImage>或使用其他<xref:System.Windows.Media.Imaging.BitmapSource>对象如<xref:System.Windows.Media.Imaging.CroppedBitmap>或<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>。 上述图像转换可以缩放或旋转图像、更改图像的像素格式或剪切图像。  
  
 使用执行图像旋转<xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A>属性的<xref:System.Windows.Media.Imaging.BitmapImage>。 只能以 90 度为增量进行旋转。 在以下示例中，图像旋转了 90 度。  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 将图像转换为不同的像素格式，如灰度使用<xref:System.Windows.Media.Imaging.FormatConvertedBitmap>。 在以下示例中，图像转换为<xref:System.Windows.Media.PixelFormats.Gray4%2A>。  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 若要裁剪图像，或者<xref:System.Windows.UIElement.Clip%2A>的属性<xref:System.Windows.Controls.Image>或<xref:System.Windows.Media.Imaging.CroppedBitmap>可用。 通常情况下，如果只是想要显示的图像的一部分<xref:System.Windows.UIElement.Clip%2A>应使用。 如果需要编码和保存剪切后的图像，<xref:System.Windows.Media.Imaging.CroppedBitmap>应使用。 在以下示例中，使用剪辑属性使用剪切图像<xref:System.Windows.Media.EllipseGeometry>。  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>拉伸图像  
 <xref:System.Windows.Controls.Image.Stretch%2A>属性控制如何拉伸图像以填充其容器。 <xref:System.Windows.Controls.Image.Stretch%2A>属性接受以下值，通过定义<xref:System.Windows.Media.Stretch>枚举：  
  
-   <xref:System.Windows.Media.Stretch.None>:不拉伸图像以填充输出区域。 如果图像比输出区域大，将图像绘制到输出区域，剪裁掉无法容纳的内容。  
  
-   <xref:System.Windows.Media.Stretch.Fill>:缩放图像以适应输出区域。 由于图像的高度和宽度独立进行缩放，因此图像的原始纵横比可能不会保留。 也就是说，为了完全填充输出容器，图像可能会扭曲。  
  
-   <xref:System.Windows.Media.Stretch.Uniform>:缩放图像，使其完全适应输出区域。 图像的纵横比会保留。  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>:缩放图像，使其在保留图像的原始纵横比的同时完全填充输出区域。  
  
 下面的示例应用每个可用<xref:System.Windows.Media.Stretch>到枚举<xref:System.Windows.Controls.Image>。  
  
 下图显示了示例的输出，并演示了不同<xref:System.Windows.Controls.Image.Stretch%2A>时必须设置应用到图像。  
  
 ![Different TileBrush Stretch settings](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
不同的拉伸设置  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>使用图像进行绘制  
 映像还在应用程序与进行绘制，从而显示<xref:System.Windows.Media.Brush>。 借助画笔，可以利用任意内容（从简单的纯色到复杂的图案和图像集）绘制 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 对象。 若要绘制图像，请使用<xref:System.Windows.Media.ImageBrush>。 <xref:System.Windows.Media.ImageBrush>是一种<xref:System.Windows.Media.TileBrush>其内容定义为位图图像。 <xref:System.Windows.Media.ImageBrush>显示由指定的单个映像及其<xref:System.Windows.Media.ImageBrush.ImageSource%2A>属性。 可以控制图像的拉伸、对齐和平铺方式，从而防止失真并生成图案和其他效果。 下图显示了可以使用实现某些效果<xref:System.Windows.Media.ImageBrush>。  
  
 ![ImageBrush 输出示例](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
图像画笔可以填充形状、控件、文本等  
  
 下面的示例演示了如何绘制一个具有映像使用的按钮的背景<xref:System.Windows.Media.ImageBrush>。  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 有关其他信息<xref:System.Windows.Media.ImageBrush>，并绘制图像查看[使用图像、 绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>图像元数据  
 某些图像文件包含用于描述文件的内容或特征的元数据。 例如，大多数数数字相机创建的图像中包含用于捕获该图像的照相机品牌和型号的元数据。 每种图像格式处理元数据的方式不同，但 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 为存储和检索每种受支持图像格式的元数据提供了一种统一方式。  
  
 通过提供对元数据的访问<xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>属性的<xref:System.Windows.Media.Imaging.BitmapSource>对象。 <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> 返回<xref:System.Windows.Media.Imaging.BitmapMetadata>包括所有所包含的图像的元数据的对象。 此数据可以位于一个元数据架构中或位于不同架构的组合中。 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 支持以下图像元数据架构： [!INCLUDE[TLA#tla_exif](../../../../includes/tlasharptla-exif-md.md)]，文字 （PNG 文本数据） [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)]， [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)]，和[!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)]。  
  
 为了简化读取元数据的过程<xref:System.Windows.Media.Imaging.BitmapMetadata>提供了可以如轻松访问的多个命名的属性<xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>， <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>，和<xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>。 许多命名属性还可以用于编写元数据。 元数据查询读取器提供对读取元数据的其他支持。 <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>方法用于检索元数据查询读取器通过提供字符串查询，如 *"/ app1/exif /"*。 在以下示例中，<xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A>用于获取存储在文本 *"/text/description"* 位置。  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 若要编写元数据，请使用元数据查询编写器。 <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> 获取查询编写器并设置所需的值。 在以下示例中，<xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>用于写入中存储的文本 *"/text/description"* 位置。  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>编解码器扩展性  
 [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] 的核心功能是用于新图像编解码器的扩展性模型。 通过这些非托管的接口，编解码器开发人员可以将编解码器与 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 集成，这样 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 应用程序就可以自动使用新的图像格式。  
  
 有关扩展性 [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] 的示例，请参阅 [Win32 示例编解码器](https://go.microsoft.com/fwlink/?LinkID=160052)。 此示例演示如何为自定义图像格式创建解码器和编码器。  
  
> [!NOTE]
>  编解码器必须进行数字签名，系统才能够识别它。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [二维图形和图像处理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Win32 示例编解码器](https://go.microsoft.com/fwlink/?LinkID=160052)
