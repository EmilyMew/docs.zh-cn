---
title: 计时行为概述
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: c3403a8602cc874e993bd649851b77d7bf652cce
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129585"
---
# <a name="timing-behaviors-overview"></a>计时行为概述
本主题介绍动画和其他的计时行为<xref:System.Windows.Media.Animation.Timeline>对象。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>系统必备  
 若要了解本主题，应熟悉基本动画功能。 有关详细信息，请参阅[动画概述](animation-overview.md)。  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>时间线类型  
 一个<xref:System.Windows.Media.Animation.Timeline>表示的时间段。 它提供的属性让你可以指定该时间段的长度、开始时间、重复次数、该时间段内时间进度的快慢等。  
  
 从时间线类继承的类可提供附加功能，例如动画和媒体播放。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了以下<xref:System.Windows.Media.Animation.Timeline>类型。  
  
|时间线类型|描述|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|抽象基类<xref:System.Windows.Media.Animation.Timeline>生成输出值以对属性进行动画处理的对象。|  
|<xref:System.Windows.Media.MediaTimeline>|从媒体文件生成输出。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|一种<xref:System.Windows.Media.Animation.TimelineGroup>该子组和控件<xref:System.Windows.Media.Animation.Timeline>对象。|  
|<xref:System.Windows.Media.Animation.Storyboard>|一种类型的<xref:System.Windows.Media.Animation.ParallelTimeline>提供目标信息及其包含的时间线对象。|  
|<xref:System.Windows.Media.Animation.Timeline>|定义计时行为的抽象基类。|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|抽象类的<xref:System.Windows.Media.Animation.Timeline>可以包含其他对象<xref:System.Windows.Media.Animation.Timeline>对象。|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>用于控制时间线长度的属性  
 一个<xref:System.Windows.Media.Animation.Timeline>表示的时间段和时间线的长度可以描述不同的方式。 下表定义了几个用于描述时间线长度的术语。  
  
|术语|描述|属性||||  
|----------|-----------------|----------------|-|-|-|  
|简单持续时间|时间线向前迭代一次所需的时间长度。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|一次重复|时间线向前播放一次，如果它采用的时间长度<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>属性为 true 时，反向播放一次。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|活动期|时间长度所需时间线，以完成由指定的所有重复其<xref:System.Windows.Media.Animation.RepeatBehavior>属性。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>中， <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>中， <xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Duration 属性  
 如前文所述，时间线表示时间段。 该时间段的长度由时间线的<xref:System.Windows.Media.Animation.Timeline.Duration%2A>。 当时间线到达其持续时间的终点时，就会停止播放。 如果时间线具有子时间线，这些子时间线也会停止播放。 播放动画时，<xref:System.Windows.Media.Animation.Timeline.Duration%2A>指定动画需要花多长转换从其起始值为终止值。 时间线的持续时间有时称为其*简单持续时间*，以区分一次迭代的持续时间和总播放动画，包括重复的时间长度。 可以指定持续时间使用有限的时间值或特殊值<xref:System.Windows.Duration.Automatic%2A>或<xref:System.Windows.Duration.Forever%2A>。 动画的持续时间应解析为<xref:System.Windows.Duration.TimeSpan%2A>值，因此它可以在值之间转换。  
  
 下面的示例演示<xref:System.Windows.Media.Animation.DoubleAnimation>与<xref:System.Windows.Media.Animation.Timeline.Duration%2A>为五秒。  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 容器时间线，如<xref:System.Windows.Media.Animation.Storyboard>并<xref:System.Windows.Media.Animation.ParallelTimeline>，默认持续时间为<xref:System.Windows.Duration.Automatic%2A>，这意味着它们将自动结束其最后一个子级停止播放时。 下面的示例演示<xref:System.Windows.Media.Animation.Storyboard>其<xref:System.Windows.Media.Animation.Timeline.Duration%2A>解析为五秒，它所需的所有子的时间长度<xref:System.Windows.Media.Animation.DoubleAnimation>对象完成。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 通过设置<xref:System.Windows.Media.Animation.Timeline.Duration%2A>到容器时间线<xref:System.Windows.Duration.TimeSpan%2A>值，可以强制播放时间长于或短于其子<xref:System.Windows.Media.Animation.Timeline>对象的播放。 如果您设置<xref:System.Windows.Media.Animation.Timeline.Duration%2A>为值的最小长度的容器时间线的子<xref:System.Windows.Media.Animation.Timeline>对象，子<xref:System.Windows.Media.Animation.Timeline>对象也会停止播放时容器时间线。 下面的示例设置<xref:System.Windows.Media.Animation.Timeline.Duration%2A>的<xref:System.Windows.Media.Animation.Storyboard>从前面的示例为三秒。 因此，第一个<xref:System.Windows.Media.Animation.DoubleAnimation>便会停止播放三秒后，当它具有经过动画处理到 60 的目标矩形的宽度。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>RepeatBehavior 属性  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>属性的<xref:System.Windows.Media.Animation.Timeline>控制重复其简单持续时间的次数。 使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>属性，您可以指定在时间线播放的次数 (迭代<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) 或总应播放的时间长度 (重复<xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>)。 无论是哪一种情况，动画都将从头到尾运行很多次，直到完成要求的次数或经历完所需的一段时间。 默认情况下，时间线具有的迭代次数为`1.0`，这意味着它们播放一次，根本不进行重复。  
  
 下面的示例使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>属性以使<xref:System.Windows.Media.Animation.DoubleAnimation>播放两次其简单持续时间内通过指定迭代次数。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 下面的示例使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>属性以使<xref:System.Windows.Media.Animation.DoubleAnimation>播放一半其简单持续时间。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 如果您设置<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>的属性<xref:System.Windows.Media.Animation.Timeline>到<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，则<xref:System.Windows.Media.Animation.Timeline>重复进行，直到以交互方式或由计时系统停止。 下面的示例使用<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>属性以使<xref:System.Windows.Media.Animation.DoubleAnimation>无限期播放。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 有关其他示例，请参阅[重复动画](how-to-repeat-an-animation.md)。  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>AutoReverse 属性  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>属性指定是否<xref:System.Windows.Media.Animation.Timeline>每次向前迭代结束时将向后播放。 以下示例设置为<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>的属性<xref:System.Windows.Media.Animation.DoubleAnimation>到`true`; 因此，它进行动画处理，从 0 到 100，然后从 100 到零。 它的总播放时长为 10 秒。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 当你使用<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>值来指定<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>的<xref:System.Windows.Media.Animation.Timeline>并<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>属性的<xref:System.Windows.Media.Animation.Timeline>是`true`，单个重复包含一次向前迭代后跟一个向后迭代。  下面的示例设置<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>的<xref:System.Windows.Media.Animation.DoubleAnimation>从前面的示例中为<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>两个。 因此，<xref:System.Windows.Media.Animation.DoubleAnimation>播放了 20 秒： 正向五秒，反向五秒，转发 5 秒，然后再反向五秒。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 如果容器时间线具有子<xref:System.Windows.Media.Animation.Timeline>对象，它们反向当容器时间线。 有关其他示例，请参阅[指定是否时间线自动反转](how-to-specify-whether-a-timeline-automatically-reverses.md)。  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>BeginTime 属性  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>属性可用于指定当启动时间线。  时间线的开始时间相对于其父时间线。 如果开始时间为零秒，则表示其父时间线开始后，该时间线立即开始；如果开始时间为其他值，会在父时间线和子时间线的开始播放时间之间产生时间偏差。 例如，如果开始时间为两秒，则表示在其父时间线到达两秒后，该时间线才开始播放。 默认情况下，所有时间线的开始时间都为零秒。 也可以设置时间线的开始时间到`null`，这样将无法启动时间线。 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，则指定 null 使用[X:null 标记扩展](../../xaml-services/x-null-markup-extension.md)。  
  
 请注意，开始时间不是时间线重复时由于每次应用其<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>设置。 如果您要创建的动画<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>10 秒的和一个<xref:System.Windows.Media.Animation.RepeatBehavior>的<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>，会有延迟 10 秒之前该动画播放第一次，但不是后续每次重复。 但是，如果动画的父时间线重新开始或重复，则会延迟 10 秒。  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>属性可用于错开时间线。 下面的示例创建<xref:System.Windows.Media.Animation.Storyboard>具有两个子<xref:System.Windows.Media.Animation.DoubleAnimation>对象。 第一个动画<xref:System.Windows.Media.Animation.Timeline.Duration%2A>为五秒，第二个和<xref:System.Windows.Media.Animation.Timeline.Duration%2A>3 秒。 该示例设置<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>第二个<xref:System.Windows.Media.Animation.DoubleAnimation>为 5 秒，因此它将从开始播放后第一个<xref:System.Windows.Media.Animation.DoubleAnimation>结束。  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior 属性  
 当<xref:System.Windows.Media.Animation.Timeline>到达其总活动持续时间，末尾<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>属性指定它是停止还是保持其最后值。 使用动画<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>的<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>"保持"其输出值： 要进行动画处理的属性保留动画的最后一个值。 值为<xref:System.Windows.Media.Animation.FillBehavior.Stop>会导致动画停止它结束后影响其目标属性。  
  
 下面的示例创建<xref:System.Windows.Media.Animation.Storyboard>具有两个子<xref:System.Windows.Media.Animation.DoubleAnimation>对象。 这两<xref:System.Windows.Media.Animation.DoubleAnimation>对象进行动画处理<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>从 0 到 100。 <xref:System.Windows.Shapes.Rectangle>元素具有非动画的<xref:System.Windows.FrameworkElement.Width%2A>值为 500 [设备无关的像素]。  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>属性的第一个<xref:System.Windows.Media.Animation.DoubleAnimation>设置为<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>，默认值。 因此，矩形的宽度后保持为 100<xref:System.Windows.Media.Animation.DoubleAnimation>结束。  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>属性的第二个<xref:System.Windows.Media.Animation.DoubleAnimation>设置为<xref:System.Windows.Media.Animation.FillBehavior.Stop>。 因此，<xref:System.Windows.FrameworkElement.Width%2A>第二个<xref:System.Windows.Shapes.Rectangle>后还原为 500<xref:System.Windows.Media.Animation.DoubleAnimation>结束。  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>用于控制时间线速度的属性  
 <xref:System.Windows.Media.Animation.Timeline>类提供三个属性用于指定其速度：  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> -指定相对于其父级，此时时间前进速率<xref:System.Windows.Media.Animation.Timeline>。 大于 1 的值增加的速度<xref:System.Windows.Media.Animation.Timeline>及其子<xref:System.Windows.Media.Animation.Timeline>对象; 0 和 1 之间的值将减慢其速度。 一个值，该值指示<xref:System.Windows.Media.Animation.Timeline>作为其父级相同的费率进行。 <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>容器时间线的设置会影响所有子<xref:System.Windows.Media.Animation.Timeline>对象。  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – 指定的百分比<xref:System.Windows.Media.Animation.Timeline.Duration%2A>以时间线的加速所占用。 有关示例，请参见 [如何：加速或减速播放动画](how-to-accelerate-or-decelerate-an-animation.md)。 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> -指定的百分比<xref:System.Windows.Media.Animation.Timeline.Duration%2A>以时间线的所用减速。 有关示例，请参见 [如何：加速或减速播放动画](how-to-accelerate-or-decelerate-an-animation.md)。  
  
## <a name="see-also"></a>请参阅

- [动画概述](animation-overview.md)
- [动画和计时系统概述](animation-and-timing-system-overview.md)
- [计时事件概述](timing-events-overview.md)
- [帮助主题](animation-and-timing-how-to-topics.md)
- [动画计时行为示例](https://go.microsoft.com/fwlink/?LinkID=159970)
