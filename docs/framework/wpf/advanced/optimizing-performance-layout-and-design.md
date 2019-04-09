---
title: 优化性能：布局和示例
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: 8a76dd5de9f374d77345eeab3d259624546fed7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107063"
---
# <a name="optimizing-performance-layout-and-design"></a>优化性能：布局和示例
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序的设计在计算布局和验证对象引用时会产生不必要的开销，从而影响性能。 对象的构造会影响应用程序的性能特征，在运行时更是如此。  
  
 本主题提供这些方面的性能改进建议。  
  
## <a name="layout"></a>布局  
 "布局处理过程"一词描述测量和排列的成员的过程<xref:System.Windows.Controls.Panel>-派生的子级，并在其中绘制它们在屏幕上的对象的集合。 布局处理过程是一个数学密集型过程，即：集合中的子级数目越多，所需的计算量就越大。 例如，每次子<xref:System.Windows.UIElement>集合中的对象改变其位置，它可能触发一个新的布局系统传递。 由于对象特征与布局行为之间的关系非常紧密，因此有必要了解可以调用布局系统的事件类型。 应用程序将尽可能减少不必要的布局处理过程调用，从而改善性能。  
  
 布局系统对集合中的每个子成员都完成两个处理过程：测量处理过程和排列处理过程。 每个子对象提供了自己的重写的实现<xref:System.Windows.UIElement.Measure%2A>和<xref:System.Windows.UIElement.Arrange%2A>方法中，以便提供其自己特定的布局行为。 简单地说，布局是一个递归系统，实现在屏幕上对元素进行大小调整、定位和绘制。  
  
-   子<xref:System.Windows.UIElement>对象通过首先测量其核心属性来开始布局过程。  
  
-   对象的<xref:System.Windows.FrameworkElement>属性与大小，如<xref:System.Windows.FrameworkElement.Width%2A>， <xref:System.Windows.FrameworkElement.Height%2A>，和<xref:System.Windows.FrameworkElement.Margin%2A>，进行计算。  
  
-   <xref:System.Windows.Controls.Panel>-应用特定的逻辑，如<xref:System.Windows.Controls.DockPanel.Dock%2A>的属性<xref:System.Windows.Controls.DockPanel>，或<xref:System.Windows.Controls.StackPanel.Orientation%2A>属性的<xref:System.Windows.Controls.StackPanel>。  
  
-   在测量所有的子对象后，将排列或定位内容。  
  
-   将子对象集合绘制到屏幕上。  
  
 如果发生下列任一操作，将再次调用布局处理过程：  
  
-   向集合中添加了一个子对象。  
  
-   一个<xref:System.Windows.FrameworkElement.LayoutTransform%2A>应用到子对象。  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A>为子对象调用方法。  
  
-   使用影响测量或排列过程的元数据进行标记的依赖属性的值发生更改时。  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>尽可能使用最高效的面板  
 布局过程的复杂性直接取决于的布局行为<xref:System.Windows.Controls.Panel>-派生您使用的元素。 例如，<xref:System.Windows.Controls.Grid>或<xref:System.Windows.Controls.StackPanel>控件提供了更多的功能比<xref:System.Windows.Controls.Canvas>控件。 功能大幅度改进的代价是性能成本的大幅度提高。 但是，如果您不需要的功能，<xref:System.Windows.Controls.Grid>控件提供了应使用成本较低的替代方法，如<xref:System.Windows.Controls.Canvas>或自定义面板。  
  
 有关详细信息，请参阅[面板概述](../controls/panels-overview.md)。  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>更新而不替换 RenderTransform  
 您可能无法在更新<xref:System.Windows.Media.Transform>而不是替换的值作为<xref:System.Windows.UIElement.RenderTransform%2A>属性。 在涉及动画的方案中，尤其是这样。 通过更新现有<xref:System.Windows.Media.Transform>，可以避免启动不需要的布局计算。  
  
### <a name="build-your-tree-top-down"></a>从上到下生成树  
 在逻辑树中添加或删除节点时，会在该节点的父级及其所有子级上引起属性失效。 因此，应始终遵循从上到下的构造模式，以避免由于在经过验证的节点中出现不必要的失效而付出代价。 下表显示了执行速度之间构建树自上而下与自下而上，其中树有 150 级深与单个差异<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Controls.DockPanel>每个级别。  
  
|**操作**|**构建树 （以毫秒为单位）**|**呈现-包括生成树 （以毫秒为单位）**|  
|----------------|---------------------------------|-------------------------------------------------|  
|从下到上|366|454|  
|从上到下|11|96|  
  
 以下代码示例演示如何从上到下创建树。  
  
 [!code-csharp[Performance#PerformanceSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 有关逻辑树的详细信息，请参阅 [WPF 中的树](trees-in-wpf.md)。  
  
## <a name="see-also"></a>请参阅

- [优化 WPF 应用程序性能](optimizing-wpf-application-performance.md)
- [规划应用程序性能](planning-for-application-performance.md)
- [利用硬件](optimizing-performance-taking-advantage-of-hardware.md)
- [二维图形和图像处理](optimizing-performance-2d-graphics-and-imaging.md)
- [对象行为](optimizing-performance-object-behavior.md)
- [应用程序资源](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [数据绑定](optimizing-performance-data-binding.md)
- [其他性能建议](optimizing-performance-other-recommendations.md)
- [布局](layout.md)
