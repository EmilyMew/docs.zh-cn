---
title: 如何：使用 CompositionTarget 按每帧间隔呈现
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 00b416d423a4bdc8bab576add2d77fd305ea6e0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089407"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>如何：使用 CompositionTarget 按每帧间隔呈现
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 动画引擎提供了许多用于创建基于帧的动画的功能。 但是，在某些应用程序方案中，需要基于每个帧以更细的粒度控制呈现。 <xref:System.Windows.Media.CompositionTarget>对象提供了创建基于每帧回调的自定义动画的功能。  
  
 <xref:System.Windows.Media.CompositionTarget> 是一个静态类，表示其绘制你的应用程序的显示图面。 <xref:System.Windows.Media.CompositionTarget.Rendering>绘制应用程序的场景每次都会引发事件。 呈现帧速率是指每秒绘制场景的次数。  
  
> [!NOTE]
>  有关完整的代码示例使用<xref:System.Windows.Media.CompositionTarget>，请参阅[使用 CompositionTarget 示例](https://go.microsoft.com/fwlink/?LinkID=160045)。  
  
## <a name="example"></a>示例  
 <xref:System.Windows.Media.CompositionTarget.Rendering>事件中，会激发[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]渲染过程。 下面的示例演示如何注册<xref:System.EventHandler>委托给静态<xref:System.Windows.Media.CompositionTarget.Rendering>方法<xref:System.Windows.Media.CompositionTarget>。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 可以使用呈现事件处理程序方法来创建自定义绘图内容。 每帧调用一次此事件处理程序方法。 每次 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 将可视化树中的持久呈现数据封送到组合场景图中时，都会调用事件处理程序方法。 另外，如果对可视化树的更改强制更新组合场景图，也会调用事件处理程序方法。 请注意，计算布局后会调用事件处理程序方法。 但是，可以修改事件处理程序方法中的布局，这意味着在呈现之前将再计算一次布局。  
  
 下面的示例演示如何提供自定义绘图<xref:System.Windows.Media.CompositionTarget>事件处理程序方法。 在此情况下，背景色的<xref:System.Windows.Controls.Canvas>使用颜色值基于鼠标的坐标位置绘制。 如果在将鼠标移动<xref:System.Windows.Controls.Canvas>，将其背景颜色更改。 另外，将基于当前的运行时间和所呈现的帧总数来计算平均帧速率。  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 可能会发现自定义绘图在不同计算机上以不同的速度运行。 这是由于自定义绘图与帧速率有关。 具体取决于您运行的系统和该系统的工作负荷<xref:System.Windows.Media.CompositionTarget.Rendering>事件不能调用不同数量的每秒的时间。 有关为运行 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序的设备确定图形硬件功能和性能的信息，请参阅[图形呈现层](../advanced/graphics-rendering-tiers.md)。  
  
 添加或删除呈现<xref:System.EventHandler>委托引发事件时将会延迟，直至完成事件后激发。 这是如何与一致<xref:System.MulticastDelegate>-基于的事件的处理在公共语言运行时 (CLR)。 另请注意，无法保证按照任何特定顺序来调用呈现事件。 如果有多个<xref:System.EventHandler>委托依赖特定的顺序，则应注册一个<xref:System.Windows.Media.CompositionTarget.Rendering>委托按正确顺序自己的事件和多路复用。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Media.CompositionTarget>
- [WPF 图形呈现疑难解答](wpf-graphics-rendering-overview.md)
