---
title: 绘制格式化文本
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: a61031c36dea84449ad07175287bf834544df886
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129085"
---
# <a name="drawing-formatted-text"></a>绘制格式化文本
本主题提供的功能的概述<xref:System.Windows.Media.FormattedText>对象。 此对象为在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序中绘制文本提供低级别控制。  

## <a name="technology-overview"></a>技术概述  
 <xref:System.Windows.Media.FormattedText>对象可绘制多行文本，在其中的文本中的每个字符可以单独设置格式。 下例演示应用了多种格式的文本。  
  
 ![使用 FormattedText 对象显示的文本](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
>  对于从 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API 迁移的开发人员，[Win32 迁移](#win32_migration)一节中的表列出了 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 标志和 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的近似等效项。  
  
### <a name="reasons-for-using-formatted-text"></a>使用格式化文本的原因  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包括用于在屏幕上绘制文本的多个控件。 每个控件都面向不同的方案，并具有自己的功能和限制列表。 一般情况下，<xref:System.Windows.Controls.TextBlock>有限的文本支持是必需的例如中的简短句子时，应使用元素[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 <xref:System.Windows.Controls.Label> 需要最少的文本支持时，可以使用。 有关详细信息，请参阅 [WPF 中的文档](documents-in-wpf.md)。  
  
 <xref:System.Windows.Media.FormattedText>对象提供更大的文本格式设置功能比[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]文本控件，并可用于在你想要将文本用作装饰元素的情况下。 有关详细信息，请参阅下一节[将格式化文本转换为几何图形](#converting_formatted_text)。  
  
 此外，<xref:System.Windows.Media.FormattedText>对象可用于创建面向文本的<xref:System.Windows.Media.DrawingVisual>-派生的对象。 <xref:System.Windows.Media.DrawingVisual> 是轻量绘图类，用于呈现形状、 图像或文本。 有关详细信息，请参阅[使用 DrawingVisuals 执行测试示例](https://go.microsoft.com/fwlink/?LinkID=159994)。  
  
## <a name="using-the-formattedtext-object"></a>使用 FormattedText 对象  
 若要创建带格式的文本，请调用<xref:System.Windows.Media.FormattedText.%23ctor%2A>构造函数创建<xref:System.Windows.Media.FormattedText>对象。 创建初始格式化文本字符串后，便可应用某一范围的格式样式。  
  
 使用<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>属性可以将约束为特定宽度的文本。 文本将自动换行，避免超过指定宽度。 使用<xref:System.Windows.Media.FormattedText.MaxTextHeight%2A>属性可以将约束为特定高度的文本。 超过指定高度的文本将显示一个省略号“…”。  
  
 ![使用换行和省略号显示的文本。](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 可向一个或多个字符应用多种格式样式。 例如，您可以调用<xref:System.Windows.Media.FormattedText.SetFontSize%2A>和<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>方法来更改格式设置的文本中的前五个字符。  
  
 下面的代码示例创建<xref:System.Windows.Media.FormattedText>对象，然后向文本应用多种格式化样式。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>字号度量单位  
 中的其他文本对象如同[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]应用程序，<xref:System.Windows.Media.FormattedText>对象使用设备无关的像素作为度量单位。 但是，大多数 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] 应用程序使用点作为度量单位。 如果要在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序中以点为单位显示文本，需要将 [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] 转换为点。 以下代码示例演示如何执行此转换。  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>将格式化文本转换为几何图形  
 可以将转换到带格式的文本<xref:System.Windows.Media.Geometry>对象，它允许您创建其他类型的悦目文本。 例如，可以创建<xref:System.Windows.Media.Geometry>基于对象的轮廓上的文本字符串。  
  
 ![使用线性渐变画笔的文本轮廓](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 以下示例说明了几种通过修改已转换文本的笔划、填充和突出显示来创建悦目的视觉效果的方法。  
  
 ![对填充和笔画使用不同颜色的文本](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![笔画应用了图像画笔的文本](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![应用绘制笔画，并突出显示了图像画笔的文本](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 当文本转换为<xref:System.Windows.Media.Geometry>对象，它不再是一系列字符，不能修改文本字符串中的字符。 但是，可修改已转换文本的笔划和填充属性，以此来影响该文本的外观。 笔划是指已转换文本的轮廓；填充是指已转换文本的轮廓的内部区域。 有关详细信息，请参阅[创建轮廓文本](how-to-create-outlined-text.md)。  
  
 此外可以将转换到带格式的文本<xref:System.Windows.Media.PathGeometry>对象，并将该对象用于突出显示文本。 例如，可以应用到动画<xref:System.Windows.Media.PathGeometry>对象，以便此动画沿着格式化文本的轮廓。  
  
 下面的示例演示已转换为的格式化的文本<xref:System.Windows.Media.PathGeometry>对象。 经过动画处理的椭圆会沿着所呈现文本的笔划路径显示。  
  
 ![沿着文本路径几何图形运动的球](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
沿着文本路径几何图形运动的球  
  
 有关详细信息，请参阅[如何：为文本创建 PathGeometry 动画](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))。  
  
 您可以创建其他有趣的用法将格式化文本转换到后<xref:System.Windows.Media.PathGeometry>对象。 例如，可剪辑视频，以便在格式化文本中显示。  
  
 ![文本路径几何图形中的视频显示](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Win32 迁移  
 功能<xref:System.Windows.Media.FormattedText>用于绘制文本是类似的功能[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]DrawText 函数。 对于从 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] API 迁移的开发人员，下表列出了 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 标志和 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的近似等效项。  
  
|DrawText 标志|WPF 等效项|说明|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|使用<xref:System.Windows.Media.FormattedText.Height%2A>属性计算相应[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]DrawText y 位置。|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|使用<xref:System.Windows.Media.FormattedText.Height%2A>和<xref:System.Windows.Media.FormattedText.Width%2A>属性计算输出矩形。|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|使用<xref:System.Windows.Media.FormattedText.TextAlignment%2A>属性值设置为<xref:System.Windows.TextAlignment.Center>。|  
|DT_EDITCONTROL|None|不要求。 间距宽度和最后一行的呈现与框架编辑控件中的相同。|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|使用<xref:System.Windows.Media.FormattedText.Trimming%2A>属性的值<xref:System.Windows.TextTrimming.CharacterEllipsis>。<br /><br /> 使用<xref:System.Windows.TextTrimming.WordEllipsis>若要获取[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]DT_END_ELLIPSIS 与 DT_WORD_ELIPSIS 尾部省略号 — 在这种情况下，省略号字符仅出现在单个行上无法容纳的词语。|  
|DT_EXPAND_TABS|None|不要求。 制表符自动扩展为在每 4 个 em 后停止，这大约为 8 个与语言无关的字符的宽度。|  
|DT_EXTERNALLEADING|None|不要求。 行距中始终包括外部间隙。 使用<xref:System.Windows.Media.FormattedText.LineHeight%2A>属性以创建用户定义的行距。|  
|DT_HIDEPREFIX|None|不支持。 移除 & 从字符串构造之前<xref:System.Windows.Media.FormattedText>对象。|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|这是默认文本对齐方式。 使用<xref:System.Windows.Media.FormattedText.TextAlignment%2A>属性值设置为<xref:System.Windows.TextAlignment.Left>。 （仅限 WPF）|  
|DT_MODIFYSTRING|None|不支持。|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|剪辑不会自动发生。 如果想要剪辑文本，使用<xref:System.Windows.Media.Visual.VisualClip%2A>属性。|  
|DT_NOFULLWIDTHCHARBREAK|None|不支持。|  
|DT_NOPREFIX|None|不要求。 字符串中的“&”字符始终作为正常字符处理。|  
|DT_PATHELLIPSIS|None|使用<xref:System.Windows.Media.FormattedText.Trimming%2A>属性的值<xref:System.Windows.TextTrimming.WordEllipsis>。|  
|DT_PREFIX|None|不支持。 如果你想要使用下划线的文本，如加速键或链接，使用<xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>方法。|  
|DT_PREFIXONLY|None|不支持。|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|使用<xref:System.Windows.Media.FormattedText.TextAlignment%2A>属性值设置为<xref:System.Windows.TextAlignment.Right>。 （仅限 WPF）|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|将 <xref:System.Windows.Media.FormattedText.FlowDirection%2A> 属性设置为 <xref:System.Windows.FlowDirection.RightToLeft>。|  
|DT_SINGLELINE|None|不要求。 <xref:System.Windows.Media.FormattedText> 对象的行为作为单行控件，除非任一<xref:System.Windows.Media.FormattedText.MaxTextWidth%2A>设置属性或者文本包含回车符/换行符 (CR/LF)。|  
|DT_TABSTOP|None|不支持用户定义的制表位位置。|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|不要求。 上对齐是默认设置。 可以使用定义其他垂直定位值<xref:System.Windows.Media.FormattedText.Height%2A>属性计算相应[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]DrawText y 位置。|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|使用<xref:System.Windows.Media.FormattedText.Height%2A>属性计算相应[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]DrawText y 位置。|  
|DT_WORDBREAK|None|不要求。 自动断词与<xref:System.Windows.Media.FormattedText>对象。 无法禁用它。|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|使用<xref:System.Windows.Media.FormattedText.Trimming%2A>属性的值<xref:System.Windows.TextTrimming.WordEllipsis>。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.FormattedText>
- [WPF 中的文档](documents-in-wpf.md)
- [WPF 中的版式](typography-in-wpf.md)
- [创建空心文本](how-to-create-outlined-text.md)
- [如何：为文本创建 PathGeometry 动画](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
