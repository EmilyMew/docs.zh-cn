---
title: OpenType 字体功能
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 86921b610b4b42cfc0393af2966b70870bc650f9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104476"
---
# <a name="opentype-font-features"></a>OpenType 字体功能

本主题概述 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体技术的一些主要功能。  
  
<a name="overview"></a>   
## <a name="opentype-font-format"></a>OpenType 字体格式  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体格式是 [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)] 字体格式的扩展，添加了对 PostScript 字体数据的支持。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体格式由 [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] 和 Adobe Corporation 联合开发。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体和操作系统服务的支持[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字体为用户提供了一个简单的方法来安装和使用字体，无论字体包含[!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)]边框还是 cff (PostScript)。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体格式解决了开发人员面临的以下挑战：  
  
-   更广泛的多平台支持。  
  
-   更出色的国际字符集支持。  
  
-   更优的字体数据保护。  
  
-   更小的文件大小，让字体发布更加高效。  
  
-   更广泛的高级版式控件支持。  
  
> [!NOTE]
>  Windows SDK 包含了一组可用于 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序的示例 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体。 这些字体提供本主题余下部分所述的大多数功能。 有关详细信息，请参阅[示例 OpenType 字体包](sample-opentype-font-pack.md)。  
  
 有关 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体格式的详细信息，请参阅 [OpenType 规范](https://go.microsoft.com/fwlink/?LinkId=96731)。  
  
### <a name="advanced-typographic-extensions"></a>高级版式扩展  
 高级版式表格（[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 布局表格）扩展了具有 [!INCLUDE[TLA2#tla_truetype](../../../../includes/tla2sharptla-truetype-md.md)] 或 CFF 边框的字体的功能。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 布局字体包含其他信息进行扩展以支持高质量国际版式字体的功能。 大多数 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体仅体现全部可用 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 功能的一部分。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体提供以下功能。  
  
-   字符与字形之间的丰富映射，可支持连字、定位格式、备用项以及其他字体替换功能。  
  
-   支持二维定位和字形附加。  
  
-   字体中包含的显式脚本和语言信息，使文本处理应用程序可相应调整其行为。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 布局表格在 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 规范的[“字体文件表格”](https://www.microsoft.com/typography/otspec/otff.htm)部分中进行了更详细的描述。  
  
 本概述的其余部分介绍的广度和灵活性的一些直观有趣[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]的属性公开的功能<xref:System.Windows.Documents.Typography>对象。 有关此对象的详细信息，请参阅[版式类](#typography_class)。  
  
<a name="variants"></a>   
## <a name="variants"></a>变量  
 变量用于呈现不同的版式风格，例如上标和下标。  
  
### <a name="superscripts-and-subscripts"></a>上标和下标  
 <xref:System.Windows.Documents.Typography.Variants%2A>属性可以设置上标和下标值[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字体。  
  
 以下文本显示 Palatino Linotype 字体的上标。  
  
 ![使用 OpenType 上标的文本](./media/opentype-font-features/opentype-superscripts.gif "使用 OpenType 上标的文本")  
  
 以下标记示例演示如何定义使用的属性的 Palatino Linotype 字体的上标<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 以下文本显示 Palatino Linotype 字体的下标。  
  
 ![使用 OpenType 下标的文本](./media/opentype-font-features/opentype-subscripts.gif "使用 OpenType 下标的文本")  
  
 以下标记示例演示如何定义 Palatino Linotype 字体的使用的属性的下标<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>上标和下标的修饰用法  
 也可使用上标和下标来营造混合大小写文本的修饰效果。 以下文本显示 Palatino Linotype 字体的上标和下标文本。 注意，大写字母不受影响。  
  
 ![使用 OpenType 上标和下标的文本](./media/opentype-font-features/opentype-superscripts-subscripts.gif "使用 OpenType 上标和下标的文本")  

 以下标记示例演示如何定义上标和下标字体使用的属性的<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>   
## <a name="capitals"></a>大写字母  
 大写字母是一组以大写样式字形呈现文本的版式形式。 通常情况下，当以全大写呈现文本时，字母之间的间距可能看起来很小，字母的权重和比例看起来会很大。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 支持多种样式设置格式的大写字母，包括小体大写字母、 小号大写字母、 标题和大写字母间距。 通过这些样式格式可控制大写字母的外观。  
  
 以下文本显示 Pescadero 字体的标准大写字母，其后接样式为“SmallCaps”和“AllSmallCaps”的字母。 本例中，对所有三个单词均使用相同的字体大小。  
  
 ![使用 OpenType 大写字母的文本](./media/opentype-font-features/opentype-capitals.gif "使用 OpenType 大写字母的文本")  
  
 以下标记示例演示如何定义使用的属性的 Pescadero 字体的大写字母<xref:System.Windows.Documents.Typography>对象。 使用“SmallCaps”格式时会忽略任何前导大写字母。  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>标题大写字母  
 标题大写字母权重和比例更小，外观比普通大写字母更加雅致。 标题大写字母通常用于作为标题的大号字体中。 以下文本显示 Pescadero 字体的普通大写字母和标题大写字母。 请注意第二行文本的宽度更窄。  
  
 ![使用 OpenType 标题大写字母的文本](./media/opentype-font-features/opentype-titling-capitals.gif "使用 OpenType 标题大写字母的文本")  
  
 以下标记示例演示如何定义 Pescadero 字体使用的属性的标题大写字母<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>大写字母间距  
 大写字母间距功能让你可以在使用全大写字母文本时提供更宽的间距。 大写字母通常设计为与小写字母混合使用。 大写字母和小写字母之间看起来比较美观的间距在使用全大写字母时可能会显得过紧。 以下文本显示 Pescadero 字体的普通间距和大写字母间距。  
  
 ![使用 OpenType 大写字母间距的文本](./media/opentype-font-features/opentype-capital-spacing.gif "使用 OpenType 大写字母间距的文本 ")  
 
 以下标记示例演示如何定义使用的属性的 Pescadero 字体的大写字母间距<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>   
## <a name="ligatures"></a>连字  
 连子是为使文本更具可读性或更加美观而由两个或更多字形形成的一个单一字形。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体支持四种类型的连字：  
  
-   **标准连字**。 旨在增强可读性。 标准连字包括“fi”、“fl”和“ff”。  
  
-   **上下文连字**。 旨在通过在组成连字的字符之间提供更好的联结行为来增强可读性。  
  
-   **自由连字**。 重在修饰性，并非专为可读性而设计。  
  
-   **历史连字**。 重在历史性，并非专为可读性而设计。  
  
 以下文本显示 Pericles 字体的标准连字字形。  
  
 ![使用 OpenType 标准连字的文本](./media/opentype-font-features/opentype-standard-ligatures.gif "使用 OpenType 标准连字的文本")  
  
 以下标记示例演示如何定义使用的属性的 Pericles 字体的标准连字字形<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 以下文本显示 Pericles 字体的自由连字字形。  
  
 ![使用 OpenType 自由连字的文本](./media/opentype-font-features/opentype-discretionary-ligatures.gif "使用 OpenType 自由连字的文本")  
  
 以下标记示例演示如何定义使用的属性的 Pericles 字体的自由连字字形<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体默认启用标准连字。 例如，如果使用 Palatino Linotype 字体，则标准连字“fi”、“ff”和“fl”显示为组合字符字形。 请注意，每个标准连字的字符对之间彼此相连。  
  
 ![使用 Palatino Linotype 使用 OpenType 标准连字的文本](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "使用 Palatino Linotype 使用 OpenType 标准连字的文本")    
   
 但是，可禁用标准连字功能，从而使“ff”等标准连字显示为两个单独的字形，而不显示为一个组合字符字形。  
  
 ![文本使用禁用的 OpenType 标准连字](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "文本使用禁用的 OpenType 标准连字")  
    
 以下标记示例演示如何禁用 Palatino Linotype 字体的使用的属性的标准连字字形<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>   
## <a name="swashes"></a>花体  
 花体是使用精美修饰的装饰性字形，通常与书法相关。 以下文本显示 Pescadero 字体的标准和花体字形。  
  
 ![使用 OpenType 标准和花体字形的文本](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "使用 OpenType 标准和花体字形的文本")  

 花体通常用作事件公告等简短文章中的修饰元素。 以下文本使用花体强调事件名称的大写字母。  
  
 ![使用 OpenType 连接形式花体的文本](./media/opentype-font-features/opentype-swashes.gif "使用 OpenType 连接形式花体的文本")  
  
 以下标记示例演示如何定义字体花体，使用的属性<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>连接形式花体  
 花体字形的某些组合可能导致文本外观欠佳，例如相邻字母的下行处出现重叠。 通过连接形式花体，可使用能生成更佳外观的替代花体字形。 以下文本显示同一单词应用连接形式花体前后的外观。  
  
 ![使用 OpenType 花体的文本](./media/opentype-font-features/opentype-contextual-swashes.gif "使用 OpenType 花体的文本")  
  
 以下标记示例演示如何定义 Pescadero 字体使用的属性的上下文花体<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>   
## <a name="alternates"></a>备用项  
 备用项是可替代标准字形的字形。 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 如下面的示例中使用的 Pericles 字体的字体，可以包含可用于创建不同文本外观的备用字形。 以下文本显示 Pericles 字体的标准字形。  
  
 ![使用 OpenType 标准字形的文本](./media/opentype-font-features/opentype-standard-glyphs.gif "使用 OpenType 标准字形的文本")  

 Pericles [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体包含其他字形，可为标准自行集提供样式备用项。 以下文本显示样式备用字形。  
  
 ![使用 OpenType 样式备用字形的文本](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "使用 OpenType 样式备用字形的文本")  
  
 以下标记示例演示如何定义 Pericles 字体的使用的属性的样式备用字形<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 以下文本显示 Pericles 字体的几种其他样式备用字形。  
  
 ![使用 OpenType 样式备用字形的 Pericles 字体的文本](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Pericles 字体的使用 OpenType 样式备用字形的文本")

 以下标记示例演示如何定义其他样式备用字形。  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>随机备用连接形式  
 随机备用连接形式为单个字符提供多种备用字形。 实现脚本类型字体时，此功能可通过使用一组随机选择的外观稍有差异的字形来模拟手写内容。 以下文本使用 Lindsey 字体的随机备用连接形式。 请注意字母“a”外观稍有变化  
  
 ![使用 OpenType 随机备用连接形式的文本](./media/opentype-font-features/opentype-random-contextual-alternates.gif "使用 OpenType 随机备用连接形式的文本")  
  
 以下标记示例演示如何定义 Lindsey 字体使用的属性的随机备用<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>历史形式  
 历史形式指过去常见的版式约定。 以下文本使用 Palatino Linotype 字体的一种历史字形形式显示短语“Boston, Massachusetts”。  
  
 ![使用 OpenType 历史形式的文本](./media/opentype-font-features/opentype-historical-forms.gif "使用 OpenType 历史形式的文本")  
   
 以下标记示例演示如何定义 Palatino Linotype 字体的使用的属性的历史记录格式<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>   
## <a name="numerical-styles"></a>数字样式  
 OpenType 字体支持多种可用于文本中数值的功能。  
  
### <a name="fractions"></a>分数  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体支持分数，包括横式分数和竖式样式。  
  
 以下文本显示 Palatino Linotype 字体的分数样式。  
  
 ![文本使用 OpenType 横式分数和竖式](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "文本使用 OpenType 横式分数和竖式")  
   
 以下标记示例演示如何定义 Palatino Linotype 字体的使用的属性的分数样式<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>旧样式数字  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体支持旧样式数字格式。 此格式对于显示不再是标准样式的数字非常有用。 以下文本以 Palatino Linotype 字体的标准和旧样式数字格式显示 18 世纪日期。  
  
 ![使用 OpenType 旧样式数字的文本](./media/opentype-font-features/opentype-old-style-numerals.gif "使用 OpenType 旧样式数字的文本")  
    
 以下文本显示 Palatino Linotype 字体的标准数字，后跟旧样式数字。  
  
 ![使用 OpenType 旧样式数字集的文本](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "使用 OpenType 旧样式数字集的文本")  
  
 以下标记示例演示如何定义 Palatino Linotype 字体的使用的属性的旧样式数字<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>比例数字和表格式数字  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体支持比例和表格式数字功能，以使用数字时控制宽度对齐方式。 比例数字将每个数字视为具有不同的宽度—“1”窄于“5”。 表格式数字被视为宽度相等的数字，因此它们可垂直对齐，从而增强财务类型信息的可读性。  
  
 以下文本使用 Miramonte 字体显示第一列中的两个表格式数字。 请注意数字“5”和“1”之间的宽度差异。 第二列显示相同的两个数值，并通过使用表格式数字功能调整其宽度。  
  
 ![使用 OpenType 比例数字和表格式数字的文本](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "使用 OpenType 比例数字和表格式数字的文本")  
    
 以下标记示例演示如何定义比例数字和表格式数字 Miramonte 字体使用的属性的<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>斜线零  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] 字体支持斜线零数字格式来强调字母"O"与数字"0"之间的区别。 斜线零数字通常用于财务和商务信息中的标识符。  
  
 以下文本显示使用 Miramonte 字体的订单标识符。 第一行使用标准数字。 第二行使用斜线零数字，以便更易于与大写字母“O”进行区分。  
  
 ![文本使用 OpenType 斜线零数字](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "文本使用 OpenType 斜线零数字")  
    
 以下标记示例演示如何定义使用的属性的 Miramonte 字体的斜线零数字<xref:System.Windows.Documents.Typography>对象。  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>   
## <a name="typography-class"></a>版式类  
 <xref:System.Windows.Documents.Typography>对象公开的功能集的[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]字体支持。 通过设置的属性<xref:System.Windows.Documents.Typography>在标记中，您可以轻松地编写文档，充分利用[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]功能。  
  
 以下文本显示 Pescadero 字体的标准大写字母，其后接样式为“SmallCaps”和“AllSmallCaps”的字母。 本例中，对所有三个单词均使用相同的字体大小。  
  
 ![使用 OpenType 大写字母的文本](./media/opentype-font-features/opentype-capitals.gif "使用 OpenType 大写字母的文本")  
    
 以下标记示例演示如何定义使用的属性的 Pescadero 字体的大写字母<xref:System.Windows.Documents.Typography>对象。 使用“SmallCaps”格式时会忽略任何前导大写字母。  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 以下代码示例完成与先前的标记事例相同的任务。  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>版式类属性  
 下表列出了属性、 值和默认设置<xref:System.Windows.Documents.Typography>对象。  
  
|属性|值|默认值|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|数值 - 字节|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps> &#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; <xref:System.Windows.FontCapitals.SmallCaps> &#124; <xref:System.Windows.FontCapitals.Titling> &#124; <xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|数值 - 字节|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional> &#124; <xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full> &#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; <xref:System.Windows.FontEastAsianWidths.Quarter> &#124; <xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|数值 - 字节|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|数值 - 字节|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior> &#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; <xref:System.Windows.FontVariants.Ruby> &#124; <xref:System.Windows.FontVariants.Subscript> &#124; <xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Documents.Typography>
- [OpenType 规范](https://go.microsoft.com/fwlink/?LinkId=96731)
- [WPF 中的版式](typography-in-wpf.md)
- [示例 OpenType 字体包](sample-opentype-font-pack.md)
- [将字体与应用程序一起打包](packaging-fonts-with-applications.md)