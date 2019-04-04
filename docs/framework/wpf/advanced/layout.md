---
title: 布局
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 4c967bf34c66cd2dcc4365a2a3ec214c9bac5623
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464562"
---
# <a name="layout"></a>布局
本主题介绍 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 布局系统。 了解布局计算发生的方式和时间对于在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中创建用户界面非常重要。  
  
 本主题包含以下各节：  
  
-   [元素边界框](#LayoutSystem_BoundingBox)  
  
-   [布局系统](#LayoutSystem_Overview)  
  
-   [测量和排列子元素](#LayoutSystem_Measure_Arrange)  
  
-   [面板元素和自定义布局行为](#LayoutSystem_PanelsCustom)  
  
-   [布局性能注意事项](#LayoutSystem_Performance)  
  
-   [子像素渲染和布局舍入](#LayoutSystem_LayoutRounding)  
  
-   [后续步骤](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>元素边界框  
 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中构思布局时，了解环绕所有元素的边界框非常重要。 每个<xref:System.Windows.FrameworkElement>使用由布局系统可以认为的嵌入到布局矩形。 <xref:System.Windows.Controls.Primitives.LayoutInformation>类返回的元素布局分配或槽的边界。 通过计算可用屏幕空间、 任何约束、 特定于布局的属性 （如边距和填充） 和父的个别行为的大小来确定矩形的大小<xref:System.Windows.Controls.Panel>元素。 处理此数据时，布局系统是否可以计算的所有子级的特定位置<xref:System.Windows.Controls.Panel>。 务必要记住，大小调整特性定义父元素，如<xref:System.Windows.Controls.Border>，会影响其子级。  
  
 下图显示了一个简单的布局。  
  
 ![显示的典型网格未添加边界框的屏幕截图。](./media/layout/grid-no-bounding-box-superimpose.png)  
  
 可以通过使用以下 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 实现此布局。  
  
 [!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 将单个<xref:System.Windows.Controls.TextBlock>内承载元素<xref:System.Windows.Controls.Grid>。 而文本填充第一列，为分配的空间的左上角<xref:System.Windows.Controls.TextBlock>实际上远大。 边界框的任何<xref:System.Windows.FrameworkElement>可以通过使用来检索<xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>方法。 下图显示的边界框<xref:System.Windows.Controls.TextBlock>元素。  
  
 ![屏幕截图显示 TextBlock 的边界框现在可见。](./media/layout/visible-textblock-bounding-box.png)  
  
 黄色矩形，为分配的空间所示<xref:System.Windows.Controls.TextBlock>元素是实际上远大于显示。 其他元素添加到<xref:System.Windows.Controls.Grid>，这种分配可以收缩或扩展，具体取决于类型和添加的元素的大小。  
  
 布局槽<xref:System.Windows.Controls.TextBlock>转换成<xref:System.Windows.Shapes.Path>通过使用<xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A>方法。 此方法可用于显示元素的边界框。  
  
 [!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>布局系统  
 简单地说，布局是一个递归系统，实现对元素进行大小调整、定位和绘制。 具体而言，布局描述测量和排列的成员的过程<xref:System.Windows.Controls.Panel>元素的<xref:System.Windows.Controls.Panel.Children%2A>集合。 布局是一个密集的过程。 较大<xref:System.Windows.Controls.Panel.Children%2A>集合，必须进行计算的越多。 此外可以根据定义的布局行为引入复杂性<xref:System.Windows.Controls.Panel>拥有该集合的元素。 相对简单<xref:System.Windows.Controls.Panel>，如<xref:System.Windows.Controls.Canvas>，可以有更复杂性能明显优于<xref:System.Windows.Controls.Panel>，如<xref:System.Windows.Controls.Grid>。  
  
 每次子<xref:System.Windows.UIElement>改变其位置，它有可能触发一个新的布局系统传递。 因此，了解哪些事件会调用布局系统就很重要，因为不必要的调用可能导致应用程序性能变差。 下面描述调用布局系统时发生的过程。  
  
1.  子<xref:System.Windows.UIElement>通过首先测量其核心属性来开始布局过程。  
  
2.  大小调整属性上定义<xref:System.Windows.FrameworkElement>计算，如<xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.Height%2A>，和<xref:System.Windows.FrameworkElement.Margin%2A>。  
  
3.  <xref:System.Windows.Controls.Panel>-应用特定的逻辑，如<xref:System.Windows.Controls.Dock>方向或堆叠<xref:System.Windows.Controls.StackPanel.Orientation%2A>。  
  
4.  测量所有子级后排列内容。  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A>在屏幕上绘制集合。  
  
6.  如果其他再次调用进程<xref:System.Windows.Controls.Panel.Children%2A>添加到集合中，<xref:System.Windows.FrameworkElement.LayoutTransform%2A>应用，或<xref:System.Windows.UIElement.UpdateLayout%2A>调用方法。  
  
 以下各节更详细地定义了此过程及其调用方式。  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>测量和排列子元素  
 布局系统的每个成员完成两个传递<xref:System.Windows.Controls.Panel.Children%2A>集合、 一个测量过程和排列处理过程。 每个子<xref:System.Windows.Controls.Panel>提供其自己<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法来实现其自己特定的布局行为。  
  
 在度量值通过的每个成员<xref:System.Windows.Controls.Panel.Children%2A>来评估集合。 通过调用会开始此过程<xref:System.Windows.UIElement.Measure%2A>方法。 父级的实现中调用此方法<xref:System.Windows.Controls.Panel>元素，并不需要的布局进行显式调用。  
  
 首先，本机大小属性<xref:System.Windows.UIElement>计算，如<xref:System.Windows.UIElement.Clip%2A>和<xref:System.Windows.UIElement.Visibility%2A>。 这将生成一个名为值`constraintSize`传递给<xref:System.Windows.FrameworkElement.MeasureCore%2A>。  
  
 其次，在定义的框架属性<xref:System.Windows.FrameworkElement>进行处理，这将影响的值`constraintSize`。 这些属性通常描述基础的大小调整特性<xref:System.Windows.UIElement>，如其<xref:System.Windows.FrameworkElement.Height%2A>， <xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.Margin%2A>，和<xref:System.Windows.FrameworkElement.Style%2A>。 其中每个属性都可以更改显示元素所需的空间。 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 然后，调用`constraintSize`作为参数。  
  
> [!NOTE]
>  没有的属性之间的差异<xref:System.Windows.FrameworkElement.Height%2A>并<xref:System.Windows.FrameworkElement.Width%2A>并<xref:System.Windows.FrameworkElement.ActualHeight%2A>和<xref:System.Windows.FrameworkElement.ActualWidth%2A>。 例如，<xref:System.Windows.FrameworkElement.ActualHeight%2A>属性是基于其他高度输入和布局系统的计算的值。 值由布局系统本身基于实际呈现的传递，设置，因此可能稍微小于属性的设置值如<xref:System.Windows.FrameworkElement.Height%2A>，是作为输入更改的基础。  
>   
>  因为<xref:System.Windows.FrameworkElement.ActualHeight%2A>是计算后的值，应注意可能有多次或递增的报告更改为它作为各种操作结果由布局系统。 布局系统可能会计算子元素所需的测量空间、父元素的约束等。  
  
 测量处理过程的最终目标是让子确定其<xref:System.Windows.UIElement.DesiredSize%2A>，就会出现此期间<xref:System.Windows.FrameworkElement.MeasureCore%2A>调用。 <xref:System.Windows.UIElement.DesiredSize%2A>该值存储<xref:System.Windows.UIElement.Measure%2A>以便在内容排列传递期间使用。  
  
 通过调用开始的排列处理过程<xref:System.Windows.UIElement.Arrange%2A>方法。 期间的排列处理过程，父<xref:System.Windows.Controls.Panel>元素生成一个表示子边界的矩形。 此值传递给<xref:System.Windows.FrameworkElement.ArrangeCore%2A>方法进行处理。  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A>方法将评估<xref:System.Windows.UIElement.DesiredSize%2A>子级的计算结果可能会影响该元素的呈现的大小的任何其他边距。 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> 将生成`arrangeSize`，它会传递给<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法的<xref:System.Windows.Controls.Panel>作为参数。 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 生成`finalSize`的子级。 最后，<xref:System.Windows.FrameworkElement.ArrangeCore%2A>方法执行的最终计算的偏移量属性，如边距和对齐方式，并将子元素放在其布局槽内。 子元素不需要（并且通常不）填充整个分配空间。 然后将控件返回到父<xref:System.Windows.Controls.Panel>和布局过程已完成。  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>面板元素和自定义布局行为  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包括的一组派生的元素<xref:System.Windows.Controls.Panel>。 这些<xref:System.Windows.Controls.Panel>元素可实现许多复杂的布局。 例如，堆叠式元素可轻松实现通过使用<xref:System.Windows.Controls.StackPanel>元素，而更复杂和自由流动的布局是可能使用<xref:System.Windows.Controls.Canvas>。  
  
 下表总结了可用布局<xref:System.Windows.Controls.Panel>元素。  
  
|面板名称|描述|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|定义一个区域，在其中可以显式定位子元素的坐标相对于<xref:System.Windows.Controls.Canvas>区域。|  
|<xref:System.Windows.Controls.DockPanel>|定义一个区域，可在其中使子元素相互水平或垂直排列。|  
|<xref:System.Windows.Controls.Grid>|定义由列和行组成的灵活的网格区域。|  
|<xref:System.Windows.Controls.StackPanel>|将子元素排列成水平或垂直的一行。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|提供了一个框架，用于<xref:System.Windows.Controls.Panel>虚拟化其子数据集合的元素。 这是一个抽象类。|  
|<xref:System.Windows.Controls.WrapPanel>|按从左到右的顺序位置定位子元素，在包含框的边缘处将内容切换到下一行。 后续排序发生按顺序从上到下还是从右到左，具体取决于值<xref:System.Windows.Controls.WrapPanel.Orientation%2A>属性。|  
  
 需要使用任意预定义不可能的布局的应用程序<xref:System.Windows.Controls.Panel>元素，自定义布局行为可以通过继承自<xref:System.Windows.Controls.Panel>并重写<xref:System.Windows.FrameworkElement.MeasureOverride%2A>和<xref:System.Windows.FrameworkElement.ArrangeOverride%2A>方法。 有关示例，请参阅[自定义径向面板示例](https://go.microsoft.com/fwlink/?LinkID=159982)。  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>布局性能注意事项  
 布局是一个递归过程。 在每个子元素<xref:System.Windows.Controls.Panel.Children%2A>集合在每次调用布局系统期间得到处理。 因此，应避免在不必要时触发布局系统。 以下注意事项有助于实现更好的性能。  
  
-   应注意哪些属性值更改会强制执行布局系统的递归更新。  
  
     如果依赖属性的值可能导致布局系统被初始化，则会使用公共标志对该依赖属性进行标记。 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> 和<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>提供有关哪些属性值更改会强制执行递归的有用提示更新由布局系统。 一般情况下，可能会影响元素的边界框的大小的任何属性应具有<xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>标志设置为 true。 有关详细信息，请参阅[依赖项属性概述](dependency-properties-overview.md)。  
  
-   如果可能，请使用<xref:System.Windows.UIElement.RenderTransform%2A>而不是<xref:System.Windows.FrameworkElement.LayoutTransform%2A>。  
  
     一个<xref:System.Windows.FrameworkElement.LayoutTransform%2A>可以是非常有用的方式来影响的内容[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]。 但是，如果转换的效果不必影响其他元素的位置，它是使用<xref:System.Windows.UIElement.RenderTransform%2A>相反，因为<xref:System.Windows.UIElement.RenderTransform%2A>不会调用布局系统。 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 应用其转换和强制执行递归布局更新以受影响的元素的新位置。  
  
-   避免不必要调用<xref:System.Windows.UIElement.UpdateLayout%2A>。  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A>方法强制执行递归布局更新，并经常是不必要。 除非你确定需要进行完整更新，否则请依赖布局系统为你调用此方法。  
  
-   使用具有较大时<xref:System.Windows.Controls.Panel.Children%2A>集合，请考虑使用<xref:System.Windows.Controls.VirtualizingStackPanel>而不是正则表达式<xref:System.Windows.Controls.StackPanel>。  
  
     通过虚拟化其子集合，<xref:System.Windows.Controls.VirtualizingStackPanel>仅在当前父级的视区中的内存中保留对象。 因此，在大多数情况下，性能得到显著提高。  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>子像素渲染和布局舍入  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 图形系统使用与设备无关的单元来使分辨率和设备独立。 每个与设备无关的像素都会随着系统的 [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] 设置自动进行缩放。 这为 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序提供了不同 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 设置的适当缩放，并使应用程序自动感知 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)]。  
  
 但是，这种 [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] 无关性可能由于抗锯齿而呈现出不规则的边缘。 这些伪影通常被视为模糊或半透明边缘，当边缘的位置落在设备像素的中间而不是设备像素之间时，就可能出现。 布局系统提供了一种通过布局倒圆对此进行调整的方法。 布局舍入是布局系统在布局传递中舍入任何非整数像素值的情况。  
  
 默认情况下禁用布局舍入。 若要启用布局舍入，请设置<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>属性设置为`true`任何<xref:System.Windows.FrameworkElement>。 因为它是一个依赖属性，所以该值将传播到可视化树中的所有子级。 若要启用布局舍入为整个 UI，请设置<xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>到`true`上根容器。 有关示例，请参见 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>。  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>下一步  
 了解元素的测量和排列方式是了解布局的第一步。 有关可用的详细信息<xref:System.Windows.Controls.Panel>元素，请参阅[面板概述](../controls/panels-overview.md)。 若要更好地了解可能影响布局的各种定位属性，请参阅[对齐、边距和填充概述](alignment-margins-and-padding-overview.md)。 有关自定义的示例<xref:System.Windows.Controls.Panel>元素，请参阅[自定义径向面板示例](https://go.microsoft.com/fwlink/?LinkID=159982)。 当准备好将其全部放在轻型应用程序，请参阅[演练：我第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [面板概述](../controls/panels-overview.md)
- [对齐、边距和填充概述](alignment-margins-and-padding-overview.md)
- [布局和示例](optimizing-performance-layout-and-design.md)
