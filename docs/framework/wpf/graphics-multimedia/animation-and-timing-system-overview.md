---
title: 动画和计时系统概述
ms.date: 03/30/2017
helpviewer_keywords:
- timing system [WPF]
- animation [WPF]
ms.assetid: 172cd5a8-a333-4c81-9456-fafccc19f382
ms.openlocfilehash: f64431e7804ba6e068a3d05f512c6ead089d7712
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079313"
---
# <a name="animation-and-timing-system-overview"></a>动画和计时系统概述
本主题描述计时系统如何使用动画<xref:System.Windows.Media.Animation.Timeline>，和<xref:System.Windows.Media.Animation.Clock>类属性进行动画处理。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>系统必备  
 为了了解本主题，应该能够使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 动画来对属性进行动画处理，如[动画概述](animation-overview.md)中所述。 本主题还有助于熟悉依赖属性；有关详细信息，请参阅[依赖属性概述](../advanced/dependency-properties-overview.md)。  
  
<a name="timelinesandclocks"></a>   
## <a name="timelines-and-clocks"></a>时间线和时钟  
 [动画概述](animation-overview.md)所述方式<xref:System.Windows.Media.Animation.Timeline>表示的时间和动画段是一种<xref:System.Windows.Media.Animation.Timeline>产生输出值。 其本身而言， <xref:System.Windows.Media.Animation.Timeline>，不执行任何操作而不只是介绍了一个时间段。 时间线的<xref:System.Windows.Media.Animation.Clock>对象执行实际工作。 同样，动画并不实际属性进行动画处理： 动画类描述应如何计算输出值，但它是<xref:System.Windows.Media.Animation.Clock>创建动画促进动画输出并将其应用到属性。  
  
 一个<xref:System.Windows.Media.Animation.Clock>是一种特殊的维护与时间有关运行时的状态对象<xref:System.Windows.Media.Animation.Timeline>。 它提供对动画和计时系统至关重要的三个信息位： <xref:System.Windows.Media.Animation.Clock.CurrentTime%2A>， <xref:System.Windows.Media.Animation.Clock.CurrentProgress%2A>，和<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>。 一个<xref:System.Windows.Media.Animation.Clock>通过使用所描述的计时行为来确定其当前时间、 进度和状态及其<xref:System.Windows.Media.Animation.Timeline>: <xref:System.Windows.Media.Animation.Timeline.Duration%2A>， <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>， <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>，依次类推。  
  
 在大多数情况下，<xref:System.Windows.Media.Animation.Clock>会自动为你的时间线创建。 当您使用进行动画处理<xref:System.Windows.Media.Animation.Storyboard>或<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法中，自动为时间线和动画创建时钟并应用于其目标属性。 此外可以创建<xref:System.Windows.Media.Animation.Clock>通过使用显式<xref:System.Windows.Media.Animation.Timeline.CreateClock%2A>方法在<xref:System.Windows.Media.Animation.Timeline>。 <xref:System.Windows.Media.MediaTimeline.CreateClock%2A?displayProperty=nameWithType>方法创建的相应类型的时钟<xref:System.Windows.Media.Animation.Timeline>上调用它。 如果<xref:System.Windows.Media.Animation.Timeline>包含子时间线，它会创建<xref:System.Windows.Media.Animation.Clock>也为其对象。 得到<xref:System.Windows.Media.Animation.Clock>在匹配的结构的树中排列对象<xref:System.Windows.Media.Animation.Timeline>从中创建树对象。  
  
 不同类型的时间线具有不同类型的时钟。 下表显示<xref:System.Windows.Media.Animation.Clock>对应于一些不同的类型<xref:System.Windows.Media.Animation.Timeline>类型。  
  
|时间线类型|时钟类型|时钟用途|  
|-------------------|----------------|-------------------|  
|动画 (继承自<xref:System.Windows.Media.Animation.AnimationTimeline>)|<xref:System.Windows.Media.Animation.AnimationClock>|为依赖属性生成输出值。|  
|<xref:System.Windows.Media.MediaTimeline>|<xref:System.Windows.Media.MediaClock>|处理媒体文件。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|<xref:System.Windows.Media.Animation.ClockGroup>|分组和控制其子<xref:System.Windows.Media.Animation.Clock>对象|  
|<xref:System.Windows.Media.Animation.Storyboard>|<xref:System.Windows.Media.Animation.ClockGroup>|分组和控制其子<xref:System.Windows.Media.Animation.Clock>对象|  
  
 您可以应用任意<xref:System.Windows.Media.Animation.AnimationClock>对象通过创建到兼容的依赖属性<xref:System.Windows.Media.Animation.IAnimatable.ApplyAnimationClock%2A>方法。  
  
 需要进行大量性能的情况下，例如对大量类似对象进行动画处理管理你自己<xref:System.Windows.Media.Animation.Clock>使用可以提供性能优势。  
  
<a name="timemanager"></a>   
## <a name="clocks-and-the-time-manager"></a>时钟和时间管理器  
 当您设置中的对象有动画效果[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，它是时间管理器，用于管理<xref:System.Windows.Media.MediaPlayer.Clock%2A>为时间线创建的对象。 时间管理器是 <xref:System.Windows.Media.MediaPlayer.Clock%2A> 对象树的根，并控制该树中的时间流。  将自动为每个 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序创建时间管理器，它对于应用程序开发人员不可见。 时间管理器每秒钟“滴答”多次；每秒发生的实际滴答次数取决于可用的系统资源。 在每个滴答，时间管理器计算的所有状态<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>计时树中的对象。  
  
 下图演示时间管理器之间的关系和<xref:System.Windows.Media.Animation.AnimationClock>，和动画处理的依赖属性。  
  
 ![计时系统组件](./media/graphicsmm-clocks-1clock1prop.png "graphicsmm_clocks_1clock1prop")  
对属性进行动画处理  
  
 当时间管理器滴答时，它会更新的时间每个<xref:System.Windows.Media.Animation.ClockState.Active><xref:System.Windows.Media.Animation.Clock>应用程序中。 如果<xref:System.Windows.Media.Animation.Clock>是<xref:System.Windows.Media.Animation.AnimationClock>，它使用<xref:System.Windows.Media.Animation.AnimationTimeline.GetCurrentValue%2A>方法的<xref:System.Windows.Media.Animation.AnimationTimeline>于创建它来计算其当前输出值。 <xref:System.Windows.Media.Animation.AnimationClock>提供<xref:System.Windows.Media.Animation.AnimationTimeline>当前本地时间、 输入的值，这通常是属性的基值，与默认目标值。 检索一个经过动画处理的值时通过属性使用<xref:System.Windows.DependencyObject.GetValue%2A>方法或其 CLR 访问器，你获得的输出其<xref:System.Windows.Media.Animation.AnimationClock>。  
  
#### <a name="clock-groups"></a>时钟组  
 前面部分介绍了如何有不同类型的<xref:System.Windows.Media.Animation.Clock>时间线的不同类型的对象。 下图演示时间管理器之间的关系<xref:System.Windows.Media.Animation.ClockGroup>、 <xref:System.Windows.Media.Animation.AnimationClock>，和动画处理的依赖属性。 一个<xref:System.Windows.Media.Animation.ClockGroup>为进行分组的其他时间线，如创建<xref:System.Windows.Media.Animation.Storyboard>类，该类对动画和其他时间线。  
  
 ![计时系统组件](./media/graphicsmm-clocks-2clock1clockgroup2prop.png "graphicsmm_clocks_2clock1clockgroup2prop")  
ClockGroup  
  
#### <a name="composition"></a>撰写  
 可以将多个时钟与一个属性相关联，在这种情况下，每个时钟都将上一个时钟的输出值用作其基值。 下图显示了三个<xref:System.Windows.Media.Animation.AnimationClock>应用于相同的属性对象。 时钟1 将经过动画处理的属性的基值用作其输入，并使用该值生成输出。 时钟2 将时钟1 的输出用作其输入，并使用该值生成输出。 时钟3 将时钟2 的输出用作其输入，并使用该值生成输出。 如果多个时钟同时影响同一个属性，则认为这些时钟位于一个组合链中。  
  
 ![计时系统组件](./media/graphicsmm-clocks-2clock1prop.png "graphicsmm_clocks_2clock1prop")  
组合链  
  
 请注意，虽然在输入和输出之间创建关系<xref:System.Windows.Media.Animation.AnimationClock>中组合链中，其计时行为不会受到影响; 的对象<xref:System.Windows.Media.Animation.Clock>对象 (包括<xref:System.Windows.Media.Animation.AnimationClock>对象) 上其父级具有分层依赖性<xref:System.Windows.Media.Animation.Clock>对象。  
  
 若要将多个时钟应用于同一个属性，请使用<xref:System.Windows.Media.Animation.HandoffBehavior.Compose><xref:System.Windows.Media.Animation.HandoffBehavior>应用时<xref:System.Windows.Media.Animation.Storyboard>，动画，或<xref:System.Windows.Media.Animation.AnimationClock>。  
  
#### <a name="ticks-and-event-consolidation"></a>滴答和事件合并  
 除了计算输出值以外，时间管理器还会在它每滴答一次时执行其他工作：它会确定每个时钟的状态并根据需要引发事件。  
  
 尽管时钟周期频繁发生，但是不同时钟周期之间可能会很多操作。 例如，<xref:System.Windows.Media.Animation.Clock>可能会停止、 启动，并再次停止，在这种情况下其<xref:System.Windows.Media.Animation.Clock.CurrentState%2A>值将更改三次。 从理论上讲，<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>事件可能会引发多个时间在一个时钟周期中; 但是，计时引擎会合并事件，以便<xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated>每个滴答一次引发事件。 这适用于所有的计时事件： 针对引发一个事件最多每种类型的给定<xref:System.Windows.Media.Animation.Clock>对象。  
  
 当<xref:System.Windows.Media.Animation.Clock>切换状态并返回到其原始状态计时周期之间 (例如从<xref:System.Windows.Media.Animation.ClockState.Active>到<xref:System.Windows.Media.Animation.ClockState.Stopped>并返回到<xref:System.Windows.Media.Animation.ClockState.Active>)，仍发生关联的事件。  
  
 有关计时事件的详细信息，请参阅[计时事件概述](timing-events-overview.md)。  
  
<a name="currentvaluesbasevaluesofproperties"></a>   
## <a name="current-values-and-base-values-of-properties"></a>属性的当前值和基值  
 可进行动画处理的属性具有两个值：基值和当前值。 在将使用其 CLR 访问器的属性的设置或<xref:System.Windows.DependencyObject.SetValue%2A>方法，您并将其基值。 对于尚未进行动画处理的属性，基值和当前值相同。  
  
 当您对属性进行动画处理<xref:System.Windows.Media.Animation.AnimationClock>设置的属性*当前*值。 检索通过其 CLR 访问器的属性的值或<xref:System.Windows.DependencyObject.GetValue%2A>方法返回的输出<xref:System.Windows.Media.Animation.AnimationClock>时<xref:System.Windows.Media.Animation.AnimationClock>是<xref:System.Windows.Media.Animation.ClockState.Active>或<xref:System.Windows.Media.Animation.ClockState.Filling>。 可以使用来检索属性的基值<xref:System.Windows.Media.Animation.IAnimatable.GetAnimationBaseValue%2A>方法。  
  
## <a name="see-also"></a>请参阅

- [动画概述](animation-overview.md)
- [计时事件概述](timing-events-overview.md)
- [计时行为概述](timing-behaviors-overview.md)
