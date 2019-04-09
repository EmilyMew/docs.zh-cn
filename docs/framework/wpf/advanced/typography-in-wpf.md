---
title: WPF 中的版式
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], about typography
ms.assetid: 06cbf17b-6eff-4fe5-949d-2dd533e4e1f4
ms.openlocfilehash: 0fba0b8814597f58018c4c5feba85082ef035e1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111405"
---
# <a name="typography-in-wpf"></a>WPF 中的版式
本主题介绍 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的主要版式功能。 这些功能包括改进的文本呈现质量和性能、[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 版式支持、增强的国际文本、增强的字体支持和新的文本应用程序编程接口 (API)。  
  
<a name="Improved_Quality_and_Performance_of_Text"></a>   
## <a name="improved-quality-and-performance-of-text"></a>改进的文本质量和性能  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的文本通过 [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] 技术呈现，该技术增强了文本的清晰度和可读性。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 一种软件技术开发的[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]，可提高现有 Lcd （液晶显示），如笔记本电脑屏幕、 Pocket PC 屏幕和平板显示器上的文本的可读性。 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 使用亚像素呈现技术，允许通过将字符对齐像素的小数部分使用的真实形状到更高的保真度显示文本。 超高的分辨率增加了文本显示中细节的清晰度，使其更便于长时间阅读。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 的另一个改进是可以朝 Y 轴方向抗锯齿，使文本字符中平缓曲线的顶端和底端变得平滑。 有关 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 功能的详细信息，请参阅 [ClearType 概述](cleartype-overview.md)。  
  
 ![采用 ClearType y 向抗锯齿的文本](./media/typography-in-wpf/text-y-direction-antialiasing.gif)  
采用 ClearType y 向抗锯齿的文本  
  
 所有文本呈现管道都可以在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中实现硬件加速，前提是计算机满足所需硬件的最低要求。 不能使用硬件执行加速的呈现会退回软件呈现。 硬件加速会影响文本呈现管道的所有阶段 - 从存储单个字形、将字形组成字形串、应用效果，到向最终显示输出应用 [!INCLUDE[TLA2#tla_ct](../../../../includes/tla2sharptla-ct-md.md)] 混合算法。 有关硬件加速的详细信息，请参阅[图形呈现层](graphics-rendering-tiers.md)。  
  
 ![文本呈现管线示意图](./media/typography-in-wpf/text-rendering-pipeline.png)  
  
 此外，动画文本（无论是按字符还是按字形进行动画处理）可充分利用由 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 启用的图形硬件功能。 因此，可生成平滑的文本动画。  
  
<a name="Rich_Typography"></a>   
## <a name="rich-typography"></a>丰富的版式  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字体格式是 [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] 字体格式的扩展。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字体格式由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 和 Adobe 共同开发，可提供多种高级版式功能。 <xref:System.Windows.Documents.Typography>对象公开的许多高级功能[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]字体，如样式备用项和花体。 [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] 提供了一组具有丰富特色的 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字体示例，如 Pericles 和 Pescadero 字体。 有关详细信息，请参阅[示例 OpenType 字体包](sample-opentype-font-pack.md)。  
  
 Pericles [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 字体包含其他字形，可为标准自行集提供样式备用项。 以下文本显示样式备用字形。  
  
 ![使用 OpenType 样式备用字形的文本](./media/typography-in-wpf/opentype-stylistic-alternate-glyphs.gif "使用 OpenType 样式备用字形的文本")  
  
 花体是使用精美修饰的装饰性字形，通常与书法相关。 以下文本显示 Pescadero 字体的标准和花体字形。  
  
 ![使用 OpenType 标准和花体字形的文本](./media/typography-in-wpf/opentype-standard-swash-glyphs.gif "使用 OpenType 标准和花体字形的文本")  
  
 有关 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 功能的详细信息，请参阅 [OpenType 字体功能](opentype-font-features.md)。  
  
<a name="Enhanced_International_Text_Support"></a>   
## <a name="enhanced-international-text-support"></a>增强的国际文本支持  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通过提供以下功能来提供增强的国际文本支持：  
  
-   使用自适应测量功能，在所有书写系统中实现自动行距调整。  
  
-   对国际文本的广泛支持。 有关详细信息，请参阅 [WPF 的全球化](globalization-for-wpf.md)。  
  
-   根据不同的语言进行分行、连字和对齐。  
  
<a name="Enhanced_Font_Support"></a>   
## <a name="enhanced-font-support"></a>增强的字体支持  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通过提供以下功能来提供增强的字体支持：  
  
-   所有文本均采用 Unicode。 字体行为和选择不再需要字符集或代码页。  
  
-   字体行为与全局设置（如系统区域设置）无关。  
  
-   单独<xref:System.Windows.FontWeight>， <xref:System.Windows.FontStretch>，并<xref:System.Windows.FontStyle>类型，用于定义<xref:System.Windows.Media.FontFamily>。 因此其灵活性高于 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 编程（在这种编程环境中，使用斜体和粗体的布尔组合来定义字体系列）。  
  
-   在处理书写方向（横向与纵向）时不受字体名称的影响。  
  
-   使用复合字体技术，在可移植 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 文件中链接和回退字体。 使用复合字体可以构造全面的多语言字体。 复合字体还提供一种可避免显示缺失字形的机制。 有关详细信息，请参阅中的备注部分<xref:System.Windows.Media.FontFamily>类。  
  
-   使用一组单语言字体，根据复合字体生成国际字体。 在开发多语言字体时，该功能可节省资源成本。  
  
-   在文档中嵌入复合字体，从而能够提供文档可移植性。 有关详细信息，请参阅中的备注部分<xref:System.Windows.Media.FontFamily>类。  
  
<a name="New_Text_APIs"></a>   
## <a name="new-text-application-programming-interfaces-apis"></a>新的文本应用程序编程接口 (API)  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了多种文本[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]供开发人员在他们的应用程序中包括文本时使用。 这些 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] 分为以下三类：  
  
-   **布局和用户界面**。 [!INCLUDE[TLA#tla_gui](../../../../includes/tlasharptla-gui-md.md)] 常见的文本控件。  
  
-   **轻量文本绘制**。 可直接在对象上绘制文本。  
  
-   **高级文本格式设置**。 可实现自定义文本引擎。  
  
### <a name="layout-and-user-interface"></a>布局和用户界面  
 在最高级的功能，文本[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]提供常见[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]控件，如<xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.TextBlock>，和<xref:System.Windows.Controls.TextBox>。 这些控件提供应用程序中的基本 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 元素，并提供一种表示文本和与文本交互的简便方法。 控件，如<xref:System.Windows.Controls.RichTextBox>和<xref:System.Windows.Controls.PasswordBox>启用更高级或专用文本处理。 和类，如<xref:System.Windows.Documents.TextRange>， <xref:System.Windows.Documents.TextSelection>，和<xref:System.Windows.Documents.TextPointer>启用有用的文本操作。 这些[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控件提供属性，例如<xref:System.Windows.Controls.Control.FontFamily%2A>， <xref:System.Windows.Controls.Control.FontSize%2A>，和<xref:System.Windows.Controls.Control.FontStyle%2A>，使你能够控制用于呈现文本的字体。  
  
#### <a name="using-bitmap-effects-transforms-and-text-effects"></a>使用位图效果、转换和文本效果  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可以用来创建悦目的文本的使用位图效果、 转换和文本效果等功能。 下面的示例演示了应用于文本的典型类型的投影效果。  
  
 ![文本阴影的柔和度&#61;0.25](./media/typography-in-wpf/drop-shadow-text-effect.jpg) 
  
 下面的示例演示了应用于文本的投影效果和噪音。  
  
 ![有噪音的文本阴影](./media/typography-in-wpf/drop-shadow-noise-text.jpg) 
  
 下面的示例演示了应用于文本的外发光效果。  
  
 ![使用 OuterGlowBitmapEffect 的文本阴影](./media/typography-in-wpf/text-shadow-glow-effect.jpg)
  
 以下示例显示了应用于文本的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文本阴影](./media/typography-in-wpf/text-shadow-blur-effect.jpg)  

 下面的示例演示沿 X 轴放大 150% 得到第二行文本，沿 Y 轴放大 150% 得到第三行文本。  
  
 ![使用 ScaleTransform 缩放的文本](./media/typography-in-wpf/scaled-text-scaletransform.jpg) 
  
 以下示例演示沿 X 轴倾斜的文本。  
  
 ![使用 SkewTransform 扭曲的文本](./media/typography-in-wpf/skewed-transformed-text.jpg)
  
 一个<xref:System.Windows.Media.TextEffect>对象是一个帮助程序对象，您可以将文本数据视为文本字符串中的字符的一个或多个组。 下面的示例演示发生旋转的单个字符。 每个字符都将以 1 秒为间隔单独旋转。  
  
 ![旋转文本的文本效果屏幕快照](./media/typography-in-wpf/rotating-text-effect.jpg) 
  
#### <a name="using-flow-documents"></a>使用流文档  
 除了常见[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控件，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供用于呈现文本的布局控件-<xref:System.Windows.Documents.FlowDocument>元素。 <xref:System.Windows.Documents.FlowDocument>元素，结合<xref:System.Windows.Controls.DocumentViewer>元素，提供了一个控件，用于为大量具有不同布局要求的文本。 布局控件提供访问权限通过高级版式<xref:System.Windows.Documents.Typography>对象和其他与字体相关属性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]控件。  
  
 下面的示例演示中承载的文本内容<xref:System.Windows.Controls.FlowDocumentReader>，它提供搜索、 导航、 分页和内容缩放支持。  
  
 ![显示 OpenType 字体的屏幕截图。](./media/typography-in-wpf/typography-text-flowdocumentreader.png)
  
 有关详细信息，请参阅 [WPF 中的文档](documents-in-wpf.md)。  
  
### <a name="lightweight-text-drawing"></a>轻量文本绘制  
 您可以直接向绘制文本[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]通过使用对象<xref:System.Windows.Media.DrawingContext.DrawText%2A>方法的<xref:System.Windows.Media.DrawingContext>对象。 若要使用此方法，您创建<xref:System.Windows.Media.FormattedText>对象。 使用该对象可以绘制多行文本，可对文本中的每个字符单独设置格式。 功能<xref:System.Windows.Media.FormattedText>对象包含的许多 Windows API 中 DrawText 标志的功能。 此外，<xref:System.Windows.Media.FormattedText>对象包含省略号支持，当文本超过其边界时在其中显示一个省略号等功能。 下面的示例演示应用多种格式的文本，其中第二个和第三个单词应用了线性渐变。  
  
 ![使用 FormattedText 对象显示的文本](./media/typography-in-wpf/text-formatted-linear-gradient.jpg) 
  
 可以将转换到带格式的文本<xref:System.Windows.Media.Geometry>对象，它允许您创建其他类型的悦目文本。 例如，可以创建<xref:System.Windows.Media.Geometry>基于对象的轮廓上的文本字符串。  
  
 ![使用线性渐变画笔的文本轮廓](./media/typography-in-wpf/text-outline-linear-gradient.jpg)  
  
 以下示例说明了几种通过修改已转换文本的笔划、填充和突出显示来创建悦目的视觉效果的方法。  
  
 ![对填充和笔画使用不同颜色的文本](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![笔画应用了图像画笔的文本](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![应用绘制笔画，并突出显示了图像画笔的文本](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 有关详细信息<xref:System.Windows.Media.FormattedText>对象，请参阅[绘制格式化文本](drawing-formatted-text.md)。  
  
### <a name="advanced-text-formatting"></a>高级文本格式设置  
 在最高级的文本[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]能够通过创建自定义文本布局<xref:System.Windows.Media.TextFormatting.TextFormatter>对象中和其他类型<xref:System.Windows.Media.TextFormatting>命名空间。 <xref:System.Windows.Media.TextFormatting.TextFormatter>和关联的类可以实现支持的字符格式、 段落样式定义的自定义文本布局换行规则和其他布局功能对国际文本。 只有在极少数情况下才需要重写 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 文本布局支持的默认实现。 但是，如果要创建文本编辑控件或应用程序，则可能需要非默认的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 实现。  
  
 与传统文本不同[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]，则<xref:System.Windows.Media.TextFormatting.TextFormatter>与通过回调方法的一组文本布局客户端进行交互。 它要求客户端提供这些方法的实现中<xref:System.Windows.Media.TextFormatting.TextSource>类。 下图说明了客户端应用程序之间的文本布局交互和<xref:System.Windows.Media.TextFormatting.TextFormatter>。  
  
 ![文本布局客户端和 TextFormatter 示意图](./media/typography-in-wpf/text-layout-text-formatter-interaction.png)  
  
 有关创建自定义文本布局的详细信息，请参阅[高级文本格式设置](advanced-text-formatting.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.FormattedText>
- <xref:System.Windows.Media.TextFormatting.TextFormatter>
- [ClearType 概述](cleartype-overview.md)
- [OpenType 字体功能](opentype-font-features.md)
- [绘制格式化文本](drawing-formatted-text.md)
- [高级文本格式设置](advanced-text-formatting.md)
- [Text](optimizing-performance-text.md)
- [Microsoft 版式](https://docs.microsoft.com/typography/)
