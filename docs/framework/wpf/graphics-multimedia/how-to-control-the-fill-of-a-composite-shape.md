---
title: 如何：控制复合形状的填充
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 9b3ab1f7b81c296aa1ee766136b6c95b82cab105
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084045"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>如何：控制复合形状的填充
<xref:System.Windows.Media.GeometryGroup.FillRule%2A>的属性<xref:System.Windows.Media.GeometryGroup>或<xref:System.Windows.Media.PathGeometry>，指定用于确定给定的点是否是几何图形的一部分复合形状的"规则"。 有两个可能值<xref:System.Windows.Media.FillRule>:<xref:System.Windows.Media.FillRule.EvenOdd>和<xref:System.Windows.Media.FillRule.Nonzero>。 以下各节将介绍如何使用这两个规则。  
  
 **EvenOdd:** 此规则确定是否填充区域从该点沿任意方向绘制一条射线，然后计算给定射线相交的形状中的路径段数目。 如果此数目为奇数，那么该点则在内部；如果为偶数，则该点在外部。  
  
 例如，以下 XAML 创建的一系列同心环 （目标） 组成的复合形状<xref:System.Windows.Media.GeometryGroup.FillRule%2A>设置为<xref:System.Windows.Media.FillRule.EvenOdd>。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]  
  
 下图显示在上一个示例中创建的形状。  
  
 ![屏幕快照：Fillrule evenodd](./media/fillruleevenoddfirstone.png "FillRuleEvenOddFirstOne")  
  
 在上图中，请注意，中心和第三个环并未填充。 这是因为射线是从穿过偶数段的这两个环中的点绘制的。 请参阅下图：  
  
 ![关系图：EvenOdd 的 FillRule 属性值](./media/fillruleevenodd2.png "FillRuleEvenOdd2")  
  
 **非零值：** 此规则确定是否在路径的填充区域从该点沿任意方向绘制一条射线，并检查段形状与射线相交的位置的位置。 从零计数开始，从左到右每次添加与射线相交的一个段，然后从右到左每次减去与射线相交的一个路径段。 在对交叉点进行计数后，如果结果为零，那么该点则位于路径外。 否则，该点则在路径内。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]  
  
 使用以下示例中，值为<xref:System.Windows.Media.FillRule.Nonzero>为<xref:System.Windows.Media.GeometryGroup.FillRule%2A>因此了以下图示：  
  
 ![屏幕快照：FillRule 值 nonzero](./media/fillrulenonzero1.png "FillRuleNonZero1")  
  
 如图所示，所有环都已填充。 这是因为所有段按同一方向运行，因此从任一点绘制的射线将与一个或多个段相交，并且交点总数不会等于零。 例如，在下图中，红色箭头表示段的绘制方向，白色箭头表示从最内部环中的某一个点运行的任意一条射线。 从零值开始，对于该射线相交的每个段，会加值“1”，因为从左到右该段与该射线相交。  
  
 ![关系图：FillRule 属性值等于 NonZero](./media/fillrulenonzero2.png "FillRuleNonZero2")  
  
 若要更好地演示行为的<xref:System.Windows.Media.FillRule.Nonzero>是必需的规则与段以不同方向运行更复杂的形状。 下面的 XAML 代码与前面的示例创建字形相似，只不过它使用创建<xref:System.Windows.Media.PathGeometry>而不是<xref:System.Windows.Media.EllipseGeometry>这将创建四个同心弧而不是完全闭合的同心环。  
  
 [!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]  
  
 下图显示在上一个示例中创建的形状。  
  
 ![屏幕快照：NonZero 的 FillRule 属性值](./media/fillrulenonzero3.png "FillRuleNonZero3")  
  
 请注意，自中心数起的第三条弧未填充。 下图说明了出现这种情况的原因。 在图中，红色箭头表示绘制段的方向。 两个白色箭头表示以“未填充”区域中的某个点为起点绘制的任意两条射线。 如图所示，与给定射线路径中的段相交的该射线值的总和为零。 如上文所定义，总和为零意味着该点不是几何图形的一部分（也不是填充的一部分），而总和*不*为零（包括负值）意味着该点是几何图形的一部分。  
  
 ![关系图：NonZero 的 FillRule 属性值](./media/fillrulenonzero4.png "FillRuleNonZero4")  
  
 **注意：** 出于<xref:System.Windows.Media.FillRule>，所有形状都视为已关闭。 如果段中存在间隙，请绘制用于闭合该段的假想线。 在以上示例中，环中存在多个较小间隙。 考虑到这一点，人们可能希望穿过间隙的射线产生不同的结果，然后射线在另一个方向上运行。 下面是放大的举例说明了一种存在的这些障碍和的"假想段"(用于应用的目的绘制的段<xref:System.Windows.Media.FillRule>)，将其关闭。  
  
 ![关系图：对于 FillRule，线段总是封闭](./media/fillruleclosedshapes.png "FillRuleClosedShapes")  
  
## <a name="example"></a>示例  
  
## <a name="see-also"></a>请参阅

- [创建复合形状](how-to-create-a-composite-shape.md)
- [Geometry 概述](geometry-overview.md)
