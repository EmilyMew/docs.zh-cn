---
title: WPF 中的双向功能概述
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 575598f48b3cfdf636be78a9de6e0c9a7fd9c208
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079820"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF 中的双向功能概述
与其他任何开发平台不同[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]具有支持的双向内容快速开发的许多功能，例如，混合从左到右和从右到左同一文档中的数据。 同时，在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]创建需要双向功能，如阿拉伯语和希伯来语用户的用户的卓越的体验。  
  
 以下各节结合一些示例阐释了如何获得双向内容的最佳显示效果，并对许多双向功能进行了说明。 大多数示例使用[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]，但可以轻松地将应用到的概念C#或 Microsoft Visual Basic 代码。  

<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 基本属性，用于定义中的内容流动方向[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]应用程序是<xref:System.Windows.FrameworkElement.FlowDirection%2A>。 此属性可以设置为两个枚举值之一<xref:System.Windows.FlowDirection.LeftToRight>或<xref:System.Windows.FlowDirection.RightToLeft>。 该属性可供所有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]继承元素<xref:System.Windows.FrameworkElement>。  
  
 下面的示例设置的流方向<xref:System.Windows.Controls.TextBox>元素。  
  
 **从左到右流方向**  
  
 [!code-xaml[LTRRTL#LTR](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **从右到左的流方向**  
  
 [!code-xaml[LTRRTL#RTL](~/samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 下图显示了前面代码的呈现方式。  
    
 ![说明了不同流方向的图形。](./media/bidirectional-features-in-wpf-overview/left-right-right-left.png)  
  
 中的某个元素[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]树将继承<xref:System.Windows.FrameworkElement.FlowDirection%2A>从其容器。 在以下示例中，<xref:System.Windows.Controls.TextBlock>位于<xref:System.Windows.Controls.Grid>，后者位于<xref:System.Windows.Window>。 设置<xref:System.Windows.FrameworkElement.FlowDirection%2A>有关<xref:System.Windows.Window>意味着将为其设置<xref:System.Windows.Controls.Grid>和<xref:System.Windows.Controls.TextBlock>也。  
  
 下面的示例演示了如何设置<xref:System.Windows.FrameworkElement.FlowDirection%2A>。  
  
 [!code-xaml[FlowDirection#FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 最高级别<xref:System.Windows.Window>已<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>，因此它所包含的所有元素也都继承同一<xref:System.Windows.FrameworkElement.FlowDirection%2A>。 若要重写指定的元素<xref:System.Windows.FrameworkElement.FlowDirection%2A>，必须添加显式方向更改的第二个<xref:System.Windows.Controls.TextBlock>在前面的示例，这会更改为<xref:System.Windows.FlowDirection.LeftToRight>。 如果未<xref:System.Windows.FrameworkElement.FlowDirection%2A>定义，则默认值<xref:System.Windows.FlowDirection.LeftToRight>适用。  
  
 下图显示了上一示例的输出：

 ![说明了显式的流方向更改的图形。](./media/bidirectional-features-in-wpf-overview/explicit-direction-change.png)  

<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 许多开发平台，如[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]，[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]和 Java 对双向内容开发提供特殊支持。 标记语言，如[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]为内容编写器提供在任何所需的方向，例如显示文本时必需的标记[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]4.0 标记、 采用"rtl"或"ltr"作为值的"dir"。 此标记是类似于<xref:System.Windows.FrameworkElement.FlowDirection%2A>属性，但<xref:System.Windows.FrameworkElement.FlowDirection%2A>属性来布局文本内容的更高级的方式工作，并且可以用于文本以外的内容。  
  
 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、 一个<xref:System.Windows.Documents.FlowDocument>是一种多功能[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素，可承载文本、 表、 图像和其他元素的组合。 以下各节中的示例均使用此元素。  
  
 将文本添加到<xref:System.Windows.Documents.FlowDocument>可以用多种方式。 若要执行此操作的简单方法是通过<xref:System.Windows.Documents.Paragraph>这是用于对文本等内容进行分组的块级元素。 若要将文本添加到内联级元素的示例使用<xref:System.Windows.Documents.Span>和<xref:System.Windows.Documents.Run>。 <xref:System.Windows.Documents.Span> 是用于对其他内联元素进行分组的内联级流内容元素时<xref:System.Windows.Documents.Run>是内联级别流内容元素应包含一系列无格式文本。 一个<xref:System.Windows.Documents.Span>可以包含多个<xref:System.Windows.Documents.Run>元素。  
  
 第一个文档示例包含具有多个网络共享名称; 的文档例如`\\server1\folder\file.ext`。 无论此网络链接是包含在阿拉伯语文档还是英语文档中，建议始终以相同的方式显示它。 下图说明了如何使用 Span 元素和链接显示在阿拉伯语<xref:System.Windows.FlowDirection.RightToLeft>文档：

 ![说明了如何使用 Span 元素的图形。](./media/bidirectional-features-in-wpf-overview/flow-direction-span-element.png "FlowDocument")  
  
 由于文本是<xref:System.Windows.FlowDirection.RightToLeft>，因此所有特殊字符，如"\\"，将文本从右到左的顺序分隔。 那样会导致不正确的顺序显示的链接，因此若要解决此问题，必须嵌入文本以保留一个单独<xref:System.Windows.Documents.Run>流动<xref:System.Windows.FlowDirection.LeftToRight>。 而不是单独<xref:System.Windows.Documents.Run>为每种语言更好的方法来解决此问题是将不常使用英语文本嵌入到较大的阿拉伯语<xref:System.Windows.Documents.Span>。  
  
 下图阐释了这一点通过使用嵌入的 Span 元素中的运行元素：

 ![图阐释了运行元素嵌入在 Span 元素中。](./media/bidirectional-features-in-wpf-overview/embedded-span-element.png)  
  
 下面的示例演示了如何使用<xref:System.Windows.Documents.Run>和<xref:System.Windows.Documents.Span>文档中的元素。  
  
 [!code-xaml[RunSpan#RunSpan](~/samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span 元素  
 <xref:System.Windows.Documents.Span>元素充当具有不同流方向的文本之间的边界分隔符。  甚至<xref:System.Windows.Documents.Span>具有相同的流方向的元素将被视为具有不同的双向范围，这意味着<xref:System.Windows.Documents.Span>元素的容器中的排序<xref:System.Windows.FlowDirection>中的内容<xref:System.Windows.Documents.Span>元素遵循<xref:System.Windows.FlowDirection>的<xref:System.Windows.Documents.Span>。  
  
 下图显示了多个流方向<xref:System.Windows.Controls.TextBlock>元素。  
    
 ![说明了具有不同流方向的文本块的图形。](./media/bidirectional-features-in-wpf-overview/flow-direction-text-blocks.png)  
  
 下面的示例演示如何使用<xref:System.Windows.Documents.Span>和<xref:System.Windows.Documents.Run>元素生成上图中显示的结果。  
  
 [!code-xaml[Span#Span](~/samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 在中<xref:System.Windows.Controls.TextBlock>在示例中，元素<xref:System.Windows.Documents.Span>元素进行布局根据<xref:System.Windows.FlowDirection>其父项，但在每个文本<xref:System.Windows.Documents.Span>元素根据其自己的流<xref:System.Windows.FlowDirection>。 这适用于拉丁语和阿拉伯语，也适用于任何其他语言。  
  
### <a name="adding-xmllang"></a>添加 xml:lang  
 下图显示了另一个示例，使用数字和算术表达式，如`"200.0+21.4=221.4"`。 请注意，只有<xref:System.Windows.FlowDirection>设置。  
    
 ![显示的数字，仅通过 flowdirection 的图形。](./media/bidirectional-features-in-wpf-overview/numbers-flow-right-left.png)  
  
 此应用程序的用户将输出感到失望，即使<xref:System.Windows.FlowDirection>正确数字形状不是阿拉伯语数字应有的形状。  
  
 XAML 元素可以包括[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]属性 (`xml:lang`)，用于定义每个元素的语言。 XAML 还支持[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]语言原则，由此`xml:lang`值应用于树中的父元素由子元素。 在上一示例中，因为没有为定义一种语言<xref:System.Windows.Documents.Run>元素或其上的任何级别的元素，默认值`xml:lang`时使用的这是`en-US`的 XAML。 内部数字整理算法[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]选择数字中的相应语言 – 在这种情况下为英语。 若要使阿拉伯语数字呈现正确`xml:lang`需要设置。  
  
 下图显示了使用示例`xml:lang`添加。  
    
 ![阐释的图形从右到左流动的阿拉伯语数字。](./media/bidirectional-features-in-wpf-overview/arabic-numbers-flow-right-left.png)  
  
 下面的示例添加`xml:lang`到应用程序。  
  
 [!code-xaml[LangAttribute#LangAttribute](~/samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 请注意，许多语言具有不同`xml:lang`具体取决于目标区域，例如，值`"ar-SA"`和`"ar-EG"`表示阿拉伯语的两种变体。 前面的示例演示了需要同时定义`xml:lang`和<xref:System.Windows.FlowDirection>值。  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>非文本元素的 FlowDirection  
 <xref:System.Windows.FlowDirection> 定义不仅文本流动方式中的文本元素，但也几乎所有其他的流方向[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素。 下图演示<xref:System.Windows.Controls.ToolBar>使用水平<xref:System.Windows.Media.LinearGradientBrush>绘制其背景与左到右的渐变。  

 ![演示工具栏从左到右的渐变的图形。](./media/bidirectional-features-in-wpf-overview/toolbar-left-right-gradient.png)  
  
 设置后<xref:System.Windows.FlowDirection>到<xref:System.Windows.FlowDirection.RightToLeft>、 不仅<xref:System.Windows.Controls.ToolBar>从右到左，但即使排列按钮<xref:System.Windows.Media.LinearGradientBrush>将沿其偏移量，从右到左流动。  
  
 下图演示重新调整<xref:System.Windows.Media.LinearGradientBrush>。  
    
 ![图形显示从右到左渐变的工具栏。](./media/bidirectional-features-in-wpf-overview/toolbar-right-left-gradient.png)  
  
 下面的示例绘制<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.Controls.ToolBar>。 (若要绘制它从左到右，删除<xref:System.Windows.FlowDirection>特性，可以在<xref:System.Windows.Controls.ToolBar>。  
  
 [!code-xaml[Gradient#Gradient](~/samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection 异常  
 有少数情况下，<xref:System.Windows.FlowDirection>与预期不符。 本部分介绍其中两种异常。  
  
 **图像**  
  
 <xref:System.Windows.Controls.Image>表示显示图像的控件。 在中[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]可与<xref:System.Windows.Controls.Image.Source%2A>属性，用于定义[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]的<xref:System.Windows.Controls.Image>显示。  
  
 与其他不同[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素，<xref:System.Windows.Controls.Image>不会继承<xref:System.Windows.FlowDirection>从容器。 但是，如果<xref:System.Windows.FlowDirection>显式设置为<xref:System.Windows.FlowDirection.RightToLeft>、<xref:System.Windows.Controls.Image>水平翻转方式显示。 这可作为一种便捷功能提供给双向内容的开发人员，因为在某些情况下，水平翻转图像会达到所需的效果。  
  
 下图显示了一个翻转<xref:System.Windows.Controls.Image>。  
    
 ![阐释翻转的图像的图形。](./media/bidirectional-features-in-wpf-overview/flipped-image-example.png)  
  
 下面的示例演示<xref:System.Windows.Controls.Image>无法继承<xref:System.Windows.FlowDirection>从<xref:System.Windows.Controls.StackPanel>包含它。 **请注意**必须具有名为的文件**ms_logo.jpg** C:\ 上若要运行此示例的驱动器。  
  
 [!code-xaml[Image#Image](~/samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **请注意**包含在下载文件中的是**ms_logo.jpg**文件。 该代码假定 .jpg 文件不在项目中，而是位于 C:\ 驱动器中的某个位置。 必须将 .jpg 从项目文件复制到 C:\ 驱动器或更改代码才能在项目内查找该文件。 若要执行此更改`Source="file://c:/ms_logo.jpg"`到`Source="ms_logo.jpg"`。  
  
 **路径**  
  
 除了<xref:System.Windows.Controls.Image>，另一个值得关注的元素<xref:System.Windows.Shapes.Path>。 Path 是可用于绘制一系列连接的直线和曲线的对象。 它的行为方式类似于<xref:System.Windows.Controls.Image>有关其<xref:System.Windows.FlowDirection>，例如其<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>是的水平镜像其<xref:System.Windows.FlowDirection.LeftToRight>之一。 但是，与不同<xref:System.Windows.Controls.Image>，<xref:System.Windows.Shapes.Path>继承其<xref:System.Windows.FlowDirection>从该容器，一个不需要显式指定。  
  
 下面的示例使用 3 条线绘制简单的箭头。 第一个箭头继承<xref:System.Windows.FlowDirection.RightToLeft>流方向从<xref:System.Windows.Controls.StackPanel>，以便从右侧的根测量其起点和终点。 第二个箭头具有显式<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>右侧还会启动。 但第三个箭头的起始根位于左侧。 有关详细信息，请参阅绘制<xref:System.Windows.Media.LineGeometry>和<xref:System.Windows.Media.GeometryGroup>。  
  
 [!code-xaml[Paths#Paths](~/samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 下图显示上一示例的输出使用绘制的箭头`Path`元素：

 ![图形的阐释使用 Path 元素绘制的箭头。](./media/bidirectional-features-in-wpf-overview/arrows-drawn-path-element.png)  
  
 <xref:System.Windows.Controls.Image>并<xref:System.Windows.Shapes.Path>两个示例说明了如何[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用<xref:System.Windows.FlowDirection>。 旁边布置[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]容器内特定方向中的元素<xref:System.Windows.FlowDirection>可用于元素如<xref:System.Windows.Controls.InkPresenter>它将呈现图面上的墨迹<xref:System.Windows.Media.LinearGradientBrush>， <xref:System.Windows.Media.RadialGradientBrush>。 每当模拟从左到右行为对内容需要右到左行为反过来也一样，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供该功能。  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>数字替换  
 从历史上看，[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]支持数字替换： 允许同时在不同的区域设置之间统一这些数字的内部存储，例如，数字将存储在相同数字使用不同区域性形状的表示形式其常见的十六进制值，如 0x40、 0x41，但却根据所选语言显示。  
  
 这样，应用程序来处理而无需将它们从一种语言转换为另一个数值，例如，用户可以打开[!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]电子表格在本地化的阿拉伯语[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]，看到阿拉伯文形状在阿拉伯语中的数字，但中将其打开欧洲版本[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]看到相同数字的欧洲表示形式。 这对其他符号（如逗号分隔符和百分比符号）来说也是必需的，因为在同一文档中它们通常随数字一起出现。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 承了，并添加了更多支持允许更多的用户控制何时以及如何使用替换此功能。 虽然此功能适用于任何语言，但它对双向内容尤其有用；由于应用程序可能会在各种区域性下运行，因此针对特定语言来设置数字形状通常是应用程序开发人员所面临的难题。  
  
 在中工作的核心属性控制如何执行数字替换[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]是<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>依赖项属性。 <xref:System.Windows.Media.NumberSubstitution>类指定文本中的数字的显示方式。 它有三个定义其行为的公共属性。 下面概括了其中的每个属性。  
  
 **CultureSource:**  
  
 此属性指定如何确定数字的区域性。 它采用三个之一<xref:System.Windows.Media.NumberCultureSource>枚举值。  
  
-   重写：数字区域性是<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>属性。  
  
-   文本：数字区域性是文本运行的区域性。 在标记中，这将是`xml:lang`，或其别名`Language`属性 (<xref:System.Windows.FrameworkElement.Language%2A>或<xref:System.Windows.FrameworkContentElement.Language%2A>)。 此外，它是派生自的类的默认值<xref:System.Windows.FrameworkContentElement>。 此类类包括<xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>， <xref:System.Windows.Documents.Table?displayProperty=nameWithType>， <xref:System.Windows.Documents.TableCell?displayProperty=nameWithType> ，依此类推。  
  
-   用户：数字区域性是当前线程的区域性。 此属性是默认值的所有子类<xref:System.Windows.FrameworkElement>如<xref:System.Windows.Controls.Page>，<xref:System.Windows.Window>和<xref:System.Windows.Controls.TextBlock>。  
  
 **CultureOverride**：  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>属性时才使用<xref:System.Windows.Media.NumberSubstitution.CultureSource%2A>属性设置为<xref:System.Windows.Media.NumberCultureSource.Override>否则将忽略。 该属性指定数字区域性。 值为`null`，默认值解释为 EN-US。  
  
 **Substitution**：  
  
 此属性指定要执行的数字替换类型。 它采用以下之一<xref:System.Windows.Media.NumberSubstitutionMethod>枚举值。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>:替换方法根据数字区域性确定<xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType>属性。 这是默认设置。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>:如果数字区域性为阿拉伯语或波斯语区域性，它指定数字取决于上下文。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>:数字始终呈现为欧洲数字。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>:使用指定的区域性的数字区域性民族数字呈现数字<xref:System.Globalization.CultureInfo.NumberFormat%2A>。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>:使用数字区域性的传统数字呈现数字。 对于大多数区域性，这是与相同<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>。 但是，<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>而此值产生阿拉伯数字让所有阿拉伯语区域性产生拉丁数字让某些阿拉伯语区域性。  
  
 这些值对双向内容开发人员意味着什么？ 在大多数情况下，可能需要开发人员只需定义<xref:System.Windows.FlowDirection>以及每个文本的语言[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]元素，例如`Language="ar-SA"`并且<xref:System.Windows.Media.NumberSubstitution>逻辑负责根据正确的数字显示[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 下面的示例演示了如何使用中的阿拉伯数字和英文数字[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]应用程序运行在阿拉伯语版的[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]。  
  
 [!code-xaml[Numbers#Numbers](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 如果你正运行在阿拉伯语版的 Windows 中显示的阿拉伯数字和英文数字带有下, 图显示上一示例的输出：

 ![显示阿拉伯数字和英文数字的图形。](./media/bidirectional-features-in-wpf-overview/arabic-english-numbers.png)  
  
 <xref:System.Windows.FlowDirection>因重要这种情况下设置<xref:System.Windows.FlowDirection>到<xref:System.Windows.FlowDirection.LeftToRight>改为时会产生欧洲数字。 以下各节介绍如何在整个文档内统一显示数字。 如果未在阿拉伯语版 Windows 上运行此示例，所有数字都将显示为欧洲数字。  
  
 **定义替换规则**  
  
 在实际的应用程序中，可能需要以编程方式设置语言。 例如，想要设置`xml:lang`要使用的系统的相同属性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，或可能更改的语言，具体取决于应用程序状态。  
  
 如果你想要更改根据应用程序的状态，请提供其他功能的使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]。  
  
 首先，将设置应用程序组件的`NumberSubstitution.CultureSource="Text"`。 使用此设置可确保设置不是来自[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]的文本元素，具有"用户"为默认值，如<xref:System.Windows.Controls.TextBlock>。  
  
例如：  

```xaml  
<TextBlock
   Name="text1" NumberSubstitution.CultureSource="Text">
   1234+5679=6913
</TextBlock>
```

在相应C#代码中，设置`Language`属性，例如，若`"ar-SA"`。  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");
```

如果您需要设置`Language`属性设置为当前用户的 UI 语言使用下面的代码。  
  
```csharp
text1.Language = System.Windows.Markup.XmlLanguage.GetLanguage(System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);
```

 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 表示在运行时使用当前线程的当前区域性。  
  
 最终[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]示例应类似于下面的示例。  
  
 [!code-xaml[Numbers2#Numbers2](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 最终C#应类似于以下示例。  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 下图显示在窗口用于任一编程语言，显示阿拉伯数字的外观：
     
 ![显示阿拉伯数字的图形。](./media/bidirectional-features-in-wpf-overview/displays-arabic-numbers.png)  
  
 **使用 Substitution 属性**  
  
 的数字替换方式[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]取决于语言的文本元素并将其<xref:System.Windows.FlowDirection>。 如果<xref:System.Windows.FlowDirection>从左到右，则会呈现欧洲数字。 但是如果前面为阿拉伯语文本或语言设置为"ar"和<xref:System.Windows.FlowDirection>是<xref:System.Windows.FlowDirection.RightToLeft>，会改为呈现阿拉伯数字。  
  
 但在某些情况下，建议创建统一的应用程序，例如适用于所有用户的欧洲数字。 或格中呈现阿拉伯数字<xref:System.Windows.Documents.Table>具有特定的单元格<xref:System.Windows.Style>。 一个简单的方法是使用<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>属性。  
  
 在以下示例中，第一个<xref:System.Windows.Controls.TextBlock>不具有<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>设置属性，因此该算法会按预期方式显示阿拉伯数字。 但是在第二个<xref:System.Windows.Controls.TextBlock>，替换设置为了欧洲，重写默认值替换为阿拉伯语数字，并将显示欧洲数字。  
  
 [!code-xaml[Numbers3#Numbers3](~/samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
