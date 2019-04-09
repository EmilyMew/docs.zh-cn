---
title: 路径标记语法
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: 32eefba26b5e04370599e4c97767b6662cfd1c13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082485"
---
# <a name="path-markup-syntax"></a>路径标记语法
路径中讨论[形状和基本绘图中 WPF 概述](shapes-and-basic-drawing-in-wpf-overview.md)和[几何概述](geometry-overview.md)，但是，本主题详细介绍了功能强大且复杂的微型语言，可用于指定路径使用更简洁的几何图形[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>系统必备  
 若要了解本主题，您应该熟悉的基本功能的<xref:System.Windows.Media.Geometry>对象。 有关详细信息，请参阅[几何概述](geometry-overview.md)。  
  
<a name="abouthisdocument"></a>   
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry and PathFigureCollection Mini-Languages  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供用于描述几何路径提供微型语言的两个类：<xref:System.Windows.Media.StreamGeometry>和<xref:System.Windows.Media.PathFigureCollection>。  
  
-   您使用<xref:System.Windows.Media.StreamGeometry>微型语言设置类型的属性时<xref:System.Windows.Media.Geometry>，如<xref:System.Windows.UIElement.Clip%2A>的属性<xref:System.Windows.UIElement>或<xref:System.Windows.Shapes.Path.Data%2A>属性<xref:System.Windows.Shapes.Path>元素。 下面的示例使用属性语法创建<xref:System.Windows.Media.StreamGeometry>。  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
-   您使用<xref:System.Windows.Media.PathFigureCollection>微型语言设置时<xref:System.Windows.Media.PathGeometry.Figures%2A>属性的<xref:System.Windows.Media.PathGeometry>。 下面的示例使用特性语法来创建<xref:System.Windows.Media.PathFigureCollection>为<xref:System.Windows.Media.PathGeometry>。  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 从前面的示例中可以看出，两种微型语言非常相似。 它始终是可以使用<xref:System.Windows.Media.PathGeometry>在任何情况下，可以使用<xref:System.Windows.Media.StreamGeometry>; 因此，您应使用哪一个？ 使用<xref:System.Windows.Media.StreamGeometry>不需要创建它; 后修改的路径时使用<xref:System.Windows.Media.PathGeometry>如果需要修改的路径。  
  
 有关详细信息之间的差异<xref:System.Windows.Media.PathGeometry>并<xref:System.Windows.Media.StreamGeometry>对象，请参阅[几何概述](geometry-overview.md)。  
  
### <a name="a-note-about-white-space"></a>有关空格的注意事项  
 为简洁起见，随后的语法部分中显示一个空格，但在显示一个空格的地方，多个空格也可以接受。  
  
 两个数字实际上无需分隔逗号或空格，但这仅可以生成的字符串不明确时。 例如，`2..3`是实际的两个数字："2." 和“.3”。 同样，`2-3`是"2"和"-3"。 命令前面或后面也无需加空格。  
  
### <a name="syntax"></a>语法  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]属性使用语法<xref:System.Windows.Media.StreamGeometry>组成的可选<xref:System.Windows.Media.FillRule>值和一个或多个图说明。  
  
|StreamGeometry XAML 属性用法|  
|-----------------------------------------|  
|`<` *object* *property* `="`[ `fillRule`] `figureDescription`[ `figureDescription`]* `" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]属性使用语法<xref:System.Windows.Media.PathFigureCollection>由一个或多个图形说明组成。  
  
|PathFigureCollection XAML Attribute Usage|  
|-----------------------------------------------|  
|`<` *object* *property* `="` `figureDescription`[ `figureDescription`]* `" ... />`|  
  
|术语|描述|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> 指定是否<xref:System.Windows.Media.StreamGeometry>使用<xref:System.Windows.Media.FillRule.EvenOdd>或<xref:System.Windows.Media.FillRule.Nonzero><xref:System.Windows.Media.PathGeometry.FillRule%2A>。<br /><br /> -   `F0` 指定<xref:System.Windows.Media.FillRule.EvenOdd>填充规则。<br />-   `F1` 指定<xref:System.Windows.Media.FillRule.Nonzero>填充规则。<br /><br /> 如果省略此命令时，子路径将使用默认行为，即<xref:System.Windows.Media.FillRule.EvenOdd>。 如果指定该命令，须先设置命令。|  
|*figureDescription*|图形由一个移动命令，绘制命令和一个可选的关闭命令组成。<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|用于指定图形起点的移动命令。 请参阅[移动命令](#themovecommand)部分。|  
|*drawCommands*|用于描述图形内容的一个或多个绘图命令。 请参阅[绘制命令](#drawcommands)部分。|  
|*closeCommand*|用于关闭图形的可选关闭命令。 请参阅[关闭命令](#closecommand)部分。|  
  
<a name="themovecommand"></a>   
## <a name="move-command"></a>移动命令  
 指定新图形的起点。  
  
|语法|  
|------------|  
|`M` *startPoint*<br /><br /> - 或 -<br /><br /> `m` *startPoint*|  
  
|术语|描述|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 新图形的起点。|  
  
 大写`M`指示`startPoint`是一个绝对值; 小写字母`m`指示`startPoint`是对前一点的偏移量或 (0，0) 如果不存在。 如果在移动命令之后列出多个点，可以绘制一条连接到这些点的直线，尽管已指定了直线命令。  
  
<a name="drawcommands"></a>   
## <a name="draw-commands"></a>绘制命令  
 绘制命令可以由几个形状命令组成。 以下形状命令可用：直线、水平线、竖线、三次贝塞尔曲线、二次贝塞尔曲线、平滑三次贝塞尔曲线、平滑二次贝塞尔曲线和椭圆弧。  
  
 可以使用大写或小写字母输入每个命令：大写字母表示绝对值，小写字母表示相对值：该线段的控制点相对于前面示例的终点。 当按顺序输入多个相同类型的命令，则可以省略重复的命令输入;例如，`L 100,200 300,400`等效于`L 100,200 L 300,400`。 下表描述了**移动**并**绘制**命令。  
  
### <a name="line-command"></a>直线命令  
 在当前点和指定的终点之间创建一条直线。 `l 20 30` 并`L 20,30`是有效的示例**行**命令。  
  
|语法|  
|------------|  
|`L` *endPoint*<br /><br /> - 或 -<br /><br /> `l` *endPoint*|  
  
|术语|描述|  
|----------|-----------------|  
|*endPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 线条的终点。|  

大写`L`指示`endPoint`是一个绝对值; 小写字母`l`指示`endPoint`是对前一点的偏移量或 (0，0) 如果不存在。

### <a name="horizontal-line-command"></a>水平线命令  
 在当前点和指定的 x 坐标之间创建一条水平线。 `H 90` 是有效水平线命令的示例。

|语法|  
|------------|  
|`H`  *x*<br /><br /> - 或 -<br /><br /> `h`  *x*|  
  
|术语|描述|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 线条终点的 x 坐标。|  
  
大写`H`指示`x`是一个绝对值; 小写字母`h`指示`x`是对前一点的偏移量或 (0，0) 如果不存在。
  
### <a name="vertical-line-command"></a>竖线命令  
 在当前点和指定的 y 坐标之间创建一条竖线。 `v 90` 是有效竖线命令的示例。

|语法|  
|------------|  
|`V`  *y*<br /><br /> - 或 -<br /><br /> `v`  *y*|  
  
|术语|描述|  
|----------|-----------------|  
|*y*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 直线终点的 y 坐标。|  

大写`V`指示`y`是一个绝对值; 小写字母`v`指示`y`是对前一点的偏移量或 (0，0) 如果不存在。  
    
### <a name="cubic-bezier-curve-command"></a>三次贝塞尔曲线命令  
 通过使用两个指定的控制点创建当前点和指定的终结点之间的三次方贝塞尔曲线 (`controlPoint`1 和`controlPoint`2)。 `C 100,200 200,400 300,200` 是有效曲线命令的示例。  
  
|语法|  
|------------|  
|`C` `controlPoint`1`controlPoint`2`endPoint`<br /><br /> - 或 -<br /><br /> `c` `controlPoint`1`controlPoint`2`endPoint`|  
  
|术语|描述|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的第一个控制点，它决定曲线的起始切线。|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的第二个控制点，它决定曲线的结束切线。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制曲线将通过的点。|  
  
### <a name="quadratic-bezier-curve-command"></a>二次贝塞尔曲线命令  
 创建二次贝塞尔曲线的当前点和指定的终结点之间使用指定的控制点 (`controlPoint`)。 `q 100,200 300,200` 是有效的二次贝塞尔曲线命令的示例。  
  
|语法|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - 或 -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|术语|描述|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的控制点，它决定曲线的开始和结束切线。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制曲线将通过的点。|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>平滑三次贝塞尔曲线命令  
 在当前点和指定的终点之间创建三次贝塞尔曲线。 假设第一控制点为相对当前点前一命令的第二控制点的反射。 如果没有前一命令或如果前一命令不是三次贝塞尔曲线命令或平滑三次贝塞尔曲线命令，则假设第一个控制点与当前点重合。 第二个控制点，由指定的曲线末尾的控制点`controlPoint`2。 例如，`S 100,200 200,300`是一个有效的平滑三次方贝塞尔曲线命令。  
  
|语法|  
|------------|  
|`S` `controlPoint`2`endPoint`<br /><br /> - 或 -<br /><br /> `s` `controlPoint`2`endPoint`|  
  
|术语|描述|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的控制点，它决定曲线的结束切线。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制曲线将通过的点。|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>平滑二次贝塞尔曲线命令  
 在当前点和指定的终点之间创建二次贝塞尔曲线。 假设控制点为相对于当前点前一命令的控制点的反射。 如果没有前一命令或如果前一命令不是二次贝塞尔曲线命令或平滑二次贝塞尔曲线命令，则控制点与当前点重合。  
  
|语法|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - 或 -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|术语|描述|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的控制点，决定曲线的起点和曲线的切线。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制曲线将通过的点。|  
  
### <a name="elliptical-arc-command"></a>椭圆弧命令  
 在当前点和指定的终点之间创建一个椭圆弧。  
  
|语法|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - 或 -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|术语|描述|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> 圆弧的 x 轴和 y 轴半径。|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 椭圆的旋转，以度为单位。|  
|`isLargeArcFlag`|如果圆弧角度应为 180 度或更大，请设置为 1，否则设置为 0。|  
|`sweepDirectionFlag`|如果以正角方向绘制圆弧，请设置为 1；否则设置为 0。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制弧将通过的点。|  
  
<a name="closecommand"></a>   
## <a name="the-close-command"></a>关闭命令  
 结束当前图形，并创建一条将当前点连接到图形起点的直线。 此命令可以在图形最后一段与第一段之间创建一条连接线（角）。  
  
|语法|  
|------------|  
|`Z`<br /><br /> - 或 -<br /><br /> `z`|  

<a name="pointsyntax"></a>   
## <a name="point-syntax"></a>点语法  
 描述一个点 x 和 y 坐标位置 (0，0) 是左上的角。
  
|语法|  
|------------|  
|`x` `,` `y`<br /><br /> - 或 -<br /><br /> `x` `y`|  
  
|术语|描述|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 该点的 x 坐标。|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 该点的 y 坐标。|  
  
<a name="specialvalues"></a>   
## <a name="special-values"></a>特殊值  
 除了标准数值外，还可使用以下特殊值。 这些数值区分大小写。  
  
 无限  
 表示<xref:System.Double.PositiveInfinity?displayProperty=nameWithType>。  
  
 -Infinity  
 表示<xref:System.Double.NegativeInfinity?displayProperty=nameWithType>。  
  
 NaN  
 表示<xref:System.Double.NaN?displayProperty=nameWithType>。  
  
 也可使用科学计数法。 例如，`+1.e17`是有效的值。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [WPF 中的形状和基本图形概述](shapes-and-basic-drawing-in-wpf-overview.md)
- [Geometry 概述](geometry-overview.md)
- [帮助主题](geometries-how-to-topics.md)
