---
title: 演示图板概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 6b178ac6b93205afebb1bea45f1b7e94826cb670
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124834"
---
# <a name="storyboards-overview"></a>演示图板概述
本主题演示如何使用<xref:System.Windows.Media.Animation.Storyboard>对象来组织和应用动画。 它介绍了如何以交互方式操作<xref:System.Windows.Media.Animation.Storyboard>对象，并介绍间接属性目标语法。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>系统必备  
 若要了解本主题，应熟悉不同的动画类型及其基本功能。 有关动画的简介，请参阅[动画概述](animation-overview.md)。 还应了解如何使用附加属性。 有关附加属性的详细信息，请参阅[附加属性概述](../advanced/attached-properties-overview.md)。  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>什么是情节提要？  
 动画并非唯一有用的时间线类型。 还提供了其他时间线类来帮助组织时间线集，并将时间线应用于属性。 容器时间线派生自<xref:System.Windows.Media.Animation.TimelineGroup>类，并包含<xref:System.Windows.Media.Animation.ParallelTimeline>和<xref:System.Windows.Media.Animation.Storyboard>。  
  
 一个<xref:System.Windows.Media.Animation.Storyboard>是一种为其包含的时间线提供目标信息的容器时间线。 情节提要可以包含任何类型的<xref:System.Windows.Media.Animation.Timeline>，包括其他容器时间线和动画。 <xref:System.Windows.Media.Animation.Storyboard> 对象，可影响各种对象和属性到一个时间线树，使其易于组织和控制复杂的计时行为的线组合。 例如，假设需要一个执行以下三个操作的按钮。  
  
-   当用户选择该按钮时，按钮增大并更改颜色。  
  
-   当用户单击该按钮时，按钮缩小并恢复其原始大小。  
  
-   当该按钮变为禁用状态时，按钮缩小且不透明度缩减到 50%。  
  
 在此情况下，有多组动画适用于同一对象，并且需要根据按钮的状态在不同的时间播放它们。 <xref:System.Windows.Media.Animation.Storyboard> 可以通过对象组织动画，并将其在组中应用到一个或多个对象。  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>何处可以使用情节提要？  
 一个<xref:System.Windows.Media.Animation.Storyboard>可用于动画处理的类的依赖项属性进行动画处理 (有关如何使类可进行动画处理的详细信息，请参阅[动画概述](animation-overview.md))。 但是，由于情节提要是框架级别功能，该对象必须属于<xref:System.Windows.NameScope>的<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。  
  
 例如，可以使用<xref:System.Windows.Media.Animation.Storyboard>来执行以下操作：  
  
-   进行动画处理<xref:System.Windows.Media.SolidColorBrush>（非框架元素） 用于绘制按钮背景 (一种类型的<xref:System.Windows.FrameworkElement>)，  
  
-   进行动画处理<xref:System.Windows.Media.SolidColorBrush>（非框架元素） 用于绘制的填充<xref:System.Windows.Media.GeometryDrawing>使用 （非框架元素） 显示<xref:System.Windows.Controls.Image>(<xref:System.Windows.FrameworkElement>)。  
  
-   在代码中，进行动画处理<xref:System.Windows.Media.SolidColorBrush>还包含一个类的声明<xref:System.Windows.FrameworkElement>，则<xref:System.Windows.Media.SolidColorBrush>注册其名称与<xref:System.Windows.FrameworkElement>。  
  
 但是，您无法使用<xref:System.Windows.Media.Animation.Storyboard>进行动画处理<xref:System.Windows.Media.SolidColorBrush>，没有注册其名称与<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>，或未用于设置的属性<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>如何使用情节提要应用动画  
 若要使用<xref:System.Windows.Media.Animation.Storyboard>来组织和应用动画，您将动画添加为子时间线<xref:System.Windows.Media.Animation.Storyboard>。 <xref:System.Windows.Media.Animation.Storyboard>类提供了<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType>附加属性。 可以在动画上设置这些属性以指定其目标对象和属性。  
  
 若要将动画应用于其目标，开始时<xref:System.Windows.Media.Animation.Storyboard>使用触发器操作或方法。 在中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，则使用<xref:System.Windows.Media.Animation.BeginStoryboard>对象<xref:System.Windows.EventTrigger>， <xref:System.Windows.Trigger>，或<xref:System.Windows.DataTrigger>。 在代码中，还可以使用<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法。  
  
 下表显示了不同的位置，每个<xref:System.Windows.Media.Animation.Storyboard>开始技术支持： 每个实例、 样式、 控件模板和数据模板。 “基于实例”是指直接将动画或情节提要应用于对象实例（而不是在样式、控件模板或数据模板中应用）的技术。  
  
|情节提要开始时使用…|基于实例|样式|控件模板|数据模板|示例|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和 <xref:System.Windows.EventTrigger>|是|是|是|是|[使用情节提要对属性进行动画处理](how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和属性 <xref:System.Windows.Trigger>|否|是|是|是|[在属性值更改时触发动画](how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> 和 <xref:System.Windows.DataTrigger>|否|是|是|是|[如何：数据发生更改时触发动画](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa970679(v=vs.90))|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> 方法|是|否|否|否|[使用情节提要对属性进行动画处理](how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 下面的示例使用<xref:System.Windows.Media.Animation.Storyboard>进行动画处理<xref:System.Windows.FrameworkElement.Width%2A>的<xref:System.Windows.Shapes.Rectangle>元素和<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>用于绘制的<xref:System.Windows.Shapes.Rectangle>。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 以下各节介绍<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>和<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>中更多详细信息的附加属性。  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>以框架元素、框架内容元素和 Freezable 元素为目标  
 上一节提到过，对于要查找其目标的动画，必须知道目标的名称和要进行动画处理的属性。 指定要进行动画处理的属性也是非常简单： 只需设置<xref:System.Windows.Media.Animation.Storyboard.TargetProperty?displayProperty=nameWithType>具有要进行动画处理的属性的名称。  指定你想要对设置进行动画处理的属性的对象的名称<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>动画的属性。  
  
 有关<xref:System.Windows.Setter.TargetName%2A>属性起作用，目标的对象必须具有一个名称。 分配将名称传递给<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]不同于分配将名称传递给<xref:System.Windows.Freezable>对象。  
  
 框架元素是继承自这些类<xref:System.Windows.FrameworkElement>类。 框架元素的示例包括<xref:System.Windows.Window>， <xref:System.Windows.Controls.DockPanel>， <xref:System.Windows.Controls.Button>，和<xref:System.Windows.Shapes.Rectangle>。 实质上，所有窗口、面板和控件都是元素。 框架内容元素是继承自这些类<xref:System.Windows.FrameworkContentElement>类。 框架内容元素的示例包括<xref:System.Windows.Documents.FlowDocument>和<xref:System.Windows.Documents.Paragraph>。 如果不确定某个类型是框架元素还是框架内容元素，请查看它是否具有 Name 属性。 如果具有 Name 属性，则可能是框架元素或框架内容元素。 若要进一步确定，请检查其类型页面的“继承性分层”部分。  
  
 若要允许框架元素或框架内容元素中的目标[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，设置其<xref:System.Windows.FrameworkElement.Name%2A>属性。 在代码中，您还需要使用<xref:System.Windows.NameScope.RegisterName%2A>方法来注册该元素的名称与已创建的元素<xref:System.Windows.NameScope>。  
  
 以下示例中，来自上述示例中，将名称分配`MyRectangle` <xref:System.Windows.Shapes.Rectangle>，一种类型的<xref:System.Windows.FrameworkElement>。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 在该元素具有名称后，可以对其属性进行动画处理。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> 类型是继承自这些类<xref:System.Windows.Freezable>类。 示例<xref:System.Windows.Freezable>包括<xref:System.Windows.Media.SolidColorBrush>， <xref:System.Windows.Media.RotateTransform>，和<xref:System.Windows.Media.GradientStop>。  
  
 若要允许的目标<xref:System.Windows.Freezable>通过在动画[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，则使用[X:name 指令](../../xaml-services/x-name-directive.md)以将其分配一个名称。 在代码中，您使用<xref:System.Windows.NameScope.RegisterName%2A>方法来注册其名称与已创建的元素<xref:System.Windows.NameScope>。  
  
 以下示例将分配将名称传递给<xref:System.Windows.Freezable>对象。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 然后动画便可以该对象为目标。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> 对象使用名称范围解析<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>属性。 有关 WPF 名称范围的详细信息，请参阅 [WPF XAML 名称范围](../advanced/wpf-xaml-namescopes.md)。 如果<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>省略属性，以元素为在其上它定义，或者，如果存在样式，带样式的元素目标的动画。  
  
 有时无法将名称分配给<xref:System.Windows.Freezable>对象。 例如，如果<xref:System.Windows.Freezable>是否声明为资源或者用于在样式中设置属性值不能有一个名称。 由于该对象没有名称，因此不能直接以它为目标，但可以间接以它为目标。 下面几节描述如何使用间接目标。  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>间接目标  
 有些时候<xref:System.Windows.Freezable>动画，例如何时不能直接面向<xref:System.Windows.Freezable>是否声明为资源或者用于设置样式中的属性值。 在这些情况下，即使您不能是直接针对可以仍进行动画处理<xref:System.Windows.Freezable>对象。 而不是设置<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>属性的名称<xref:System.Windows.Freezable>，您为其提供的元素名称所属<xref:System.Windows.Freezable>"属于"。 例如，<xref:System.Windows.Media.SolidColorBrush>用于设置<xref:System.Windows.Shapes.Shape.Fill%2A>矩形内的元素属于该矩形。 若要对画笔进行动画处理，需要设置动画<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>具有起点是框架元素或框架内容元素的属性的属性链<xref:System.Windows.Freezable>用于设置和结尾<xref:System.Windows.Freezable>属性进行动画处理。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 请注意，如果<xref:System.Windows.Freezable>是冻结，则将进行克隆，并且该克隆进行动画处理。 当发生这种情况，原始对象的<xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A>属性会继续返回`false`，因为原始对象不实际进行动画处理。 有关克隆的详细信息，请参阅[Freezable 对象概述](../advanced/freezable-objects-overview.md)。  
  
 另请注意，当使用间接属性目标时，可能会以不存在的对象为目标。 例如，您可能认为<xref:System.Windows.Controls.Control.Background%2A>了特定按钮的设置与<xref:System.Windows.Media.SolidColorBrush>并尝试进行动画处理时实际上其颜色<xref:System.Windows.Media.LinearGradientBrush>用于设置按钮的背景。 在这些情况下，不会引发异常;动画不具有可视效果，因为<xref:System.Windows.Media.LinearGradientBrush>不响应更改<xref:System.Windows.Media.SolidColorBrush.Color%2A>属性。  
  
 下面几节详细介绍间接属性目标语法。  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>在 XAML 中间接以 Freezable 的属性为目标  
 为面向中以 freezable 的属性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，使用以下语法。  
  
| |  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName*的属性<xref:System.Windows.FrameworkElement>其<xref:System.Windows.Freezable>用于设置，和  
  
-   *FreezablePropertyName*的属性<xref:System.Windows.Freezable>进行动画处理。  
  
 下面的代码演示如何进行动画处理<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>用于设置  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> 矩形元素。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 有时，需要以集合或数组中包含的 Freezable 为目标。  
  
 若要以集合中包含的 Freezable 为目标，可以使用以下路径语法。  
  
| |  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 其中*CollectionIndex*是其数组或集合中对象的索引。  
  
 例如，假设矩形具有<xref:System.Windows.Media.TransformGroup>资源应用于其<xref:System.Windows.UIElement.RenderTransform%2A>属性，并且想要对它包含的转换之一进行动画处理。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 下面的代码演示如何进行动画处理<xref:System.Windows.Media.RotateTransform.Angle%2A>属性的<xref:System.Windows.Media.RotateTransform>上一示例中所示。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>在代码中间接以 Freezable 的属性为目标  
 在代码中，您创建<xref:System.Windows.PropertyPath>对象。 当您创建<xref:System.Windows.PropertyPath>，则指定<xref:System.Windows.PropertyPath.Path%2A>和<xref:System.Windows.PropertyPath.PathParameters%2A>。  
  
 若要创建<xref:System.Windows.PropertyPath.PathParameters%2A>，创建类型的数组<xref:System.Windows.DependencyProperty>包含依赖项属性标识符字段的列表。 第一个标识符字段的属性是<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>的<xref:System.Windows.Freezable>用于设置。 下一步的标识符字段表示的属性<xref:System.Windows.Freezable>到目标。 将其作为连接的属性链<xref:System.Windows.Freezable>到<xref:System.Windows.FrameworkElement>对象。  
  
 以下是针对一个依赖属性链的示例<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>用于设置<xref:System.Windows.Shapes.Shape.Fill%2A>的矩形元素。  
  
 [!code-csharp[storyboards_ovw_snip#135](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 此外需要指定<xref:System.Windows.PropertyPath.Path%2A>。 一个<xref:System.Windows.PropertyPath.Path%2A>是<xref:System.String>，它告诉<xref:System.Windows.PropertyPath.Path%2A>如何解释其<xref:System.Windows.PropertyPath.PathParameters%2A>。 它使用以下语法。  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex*的索引<xref:System.Windows.DependencyProperty>数组，其中包含的标识符<xref:System.Windows.FrameworkElement>对象的属性的<xref:System.Windows.Freezable>用于设置，和  
  
-   *FreezablePropertyArrayIndex*索引的<xref:System.Windows.DependencyProperty>数组，其中包含目标属性的标识符。  
  
 下面的示例演示<xref:System.Windows.PropertyPath.Path%2A>附带<xref:System.Windows.PropertyPath.PathParameters%2A>中前面的示例中定义。
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 下面的示例结合进行动画处理的上一示例中的代码<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>用于设置<xref:System.Windows.Shapes.Shape.Fill%2A>的矩形元素。  
  
 [!code-csharp[storyboards_ovw_snip#137](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 有时，需要以集合或数组中包含的 Freezable 为目标。 例如，假设矩形具有<xref:System.Windows.Media.TransformGroup>资源应用于其<xref:System.Windows.UIElement.RenderTransform%2A>属性，并且想要对它包含的转换之一进行动画处理。  
  
 [!code-xaml[storyboards_ovw_snip#142](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 到目标<xref:System.Windows.Freezable>包含在集合中，使用以下路径语法。  
  
| |  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 其中*CollectionIndex*是其数组或集合中对象的索引。  
  
 到目标<xref:System.Windows.Media.RotateTransform.Angle%2A>的属性<xref:System.Windows.Media.RotateTransform>中的第二个转换<xref:System.Windows.Media.TransformGroup>，会使用以下<xref:System.Windows.PropertyPath.Path%2A>和<xref:System.Windows.PropertyPath.PathParameters%2A>。  
  
 [!code-csharp[storyboards_ovw_snip#139](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 下面的示例演示对进行动画处理的完整代码<xref:System.Windows.Media.RotateTransform.Angle%2A>的<xref:System.Windows.Media.RotateTransform>中包含<xref:System.Windows.Media.TransformGroup>。  
  
 [!code-csharp[storyboards_ovw_snip#138](~/samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>间接以 Freezable 为目标并将其作为起点  
 前面几节介绍了如何以间接目标<xref:System.Windows.Freezable>作为开头<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>并创建到的属性链<xref:System.Windows.Freezable>子属性。 此外可以使用<xref:System.Windows.Freezable>作为起始点和间接目标的一个其<xref:System.Windows.Freezable>子属性。 一条附加限制适用于使用时<xref:System.Windows.Freezable>作为间接目标的起点： 起始<xref:System.Windows.Freezable>和每个<xref:System.Windows.Freezable>它与间接设定为目标的子属性之间不能冻结。  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>在 XAML 中以交互方式控制情节提要  
 若要在启动情节提要[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]，则使用<xref:System.Windows.Media.Animation.BeginStoryboard>触发操作。 <xref:System.Windows.Media.Animation.BeginStoryboard> 将动画分发到的对象和属性，它们进行动画处理，并启动情节提要。 (有关此过程的详细信息，请参阅[动画和计时系统概述](animation-and-timing-system-overview.md)。)如果您为提供<xref:System.Windows.Media.Animation.BeginStoryboard>通过指定的名称及其<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>属性，您使它可控制情节提要。 然后，可以在情节提要启动后以交互方式对它进行控制。 下面列出了可与事件触发器一起使用来控制情节提要的可控制情节提要操作。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>:暂停情节提要。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>:恢复暂停的情节提要。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>:更改情节提要的速度。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>:如果有，请转到其填充期，末尾情节提要。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>:停止情节提要。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>:删除情节提要。  
  
 在下面的示例中，使用可控制的情节提要操作来以交互方式控制情节提要。  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>使用代码以交互方式控制情节提要  
 前面的示例已演示了如何使用触发器操作进行动画处理。 在代码中，您也可以控制使用交互式方法对的情节提要<xref:System.Windows.Media.Animation.Storyboard>类。 有关<xref:System.Windows.Media.Animation.Storyboard>若要进行交互式代码中，必须使用情节提要的适当重载<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>方法并指定`true`以使其可以控制。 请参阅<xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>页，了解详细信息。  
  
 以下列表显示了可用于操作的方法<xref:System.Windows.Media.Animation.Storyboard>它启动后：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 使用这些方法的优点是不需要创建<xref:System.Windows.Trigger>或<xref:System.Windows.TriggerAction>对象; 只需对可控制引用<xref:System.Windows.Media.Animation.Storyboard>要进行处理。  
  
 **注意：** 对所执行的所有交互操作<xref:System.Windows.Media.Animation.Clock>，并因此同样，在<xref:System.Windows.Media.Animation.Storyboard>会在下一步呈现之前短暂发生在计时引擎的下一步刻度线上发生。 例如，如果您使用<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>方法跳转到动画，属性值中的另一个点不会立即更改、 的值而不是，计时引擎的下一计时周期发生更改。  
  
 下面的示例演示如何应用和控制动画使用交互式方法对的<xref:System.Windows.Media.Animation.Storyboard>类。  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>在样式中进行动画处理  
 可以使用<xref:System.Windows.Media.Animation.Storyboard>对象定义中的动画<xref:System.Windows.Style>。 进行动画处理与<xref:System.Windows.Media.Animation.Storyboard>中<xref:System.Windows.Style>类似于使用<xref:System.Windows.Media.Animation.Storyboard>在其他位置，有以下三个例外：  
  
-   未指定<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>;<xref:System.Windows.Media.Animation.Storyboard>始终以元素为向其目标<xref:System.Windows.Style>应用。 到目标<xref:System.Windows.Freezable>对象，必须使用间接目标。 有关间接目标的详细信息，请参阅[间接目标](#pathsyntaxforchangeable)部分。  
  
-   不能指定<xref:System.Windows.EventTrigger.SourceName%2A>有关<xref:System.Windows.EventTrigger>或<xref:System.Windows.Trigger>。  
  
-   不能使用动态资源引用或数据绑定表达式来设置<xref:System.Windows.Media.Animation.Storyboard>或动画属性值。 这是因为内的所有内容<xref:System.Windows.Style>必须是线程安全的计时系统必须<xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard>对象以使其变为线程安全。 一个<xref:System.Windows.Media.Animation.Storyboard>如果它或及其子时间线包含动态资源引用或数据绑定表达式不能冻结。 有关冻结和其他详细信息<xref:System.Windows.Freezable>功能，请参阅[Freezable 对象概述](../advanced/freezable-objects-overview.md)。  
  
-   在中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，不能声明为事件处理程序<xref:System.Windows.Media.Animation.Storyboard>或动画事件。  
  
 有关演示如何在样式中定义情节提要的示例，请参阅[样式中的进行动画处理](how-to-animate-in-a-style.md)示例。  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>在 ControlTemplate 中进行动画处理  
 可以使用<xref:System.Windows.Media.Animation.Storyboard>对象定义中的动画<xref:System.Windows.Controls.ControlTemplate>。 进行动画处理与<xref:System.Windows.Media.Animation.Storyboard>中<xref:System.Windows.Controls.ControlTemplate>类似于使用<xref:System.Windows.Media.Animation.Storyboard>在其他位置，使用以下两种例外情况：  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>的子对象只能引用<xref:System.Windows.Controls.ControlTemplate>。 如果<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>未指定，则动画以元素为向其目标<xref:System.Windows.Controls.ControlTemplate>应用。  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A>有关<xref:System.Windows.EventTrigger>或<xref:System.Windows.Trigger>的子对象只能引用<xref:System.Windows.Controls.ControlTemplate>。  
  
-   不能使用动态资源引用或数据绑定表达式来设置<xref:System.Windows.Media.Animation.Storyboard>或动画属性值。 这是因为内的所有内容<xref:System.Windows.Controls.ControlTemplate>必须是线程安全的计时系统必须<xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard>对象以使其变为线程安全。 一个<xref:System.Windows.Media.Animation.Storyboard>如果它或及其子时间线包含动态资源引用或数据绑定表达式不能冻结。 有关冻结和其他详细信息<xref:System.Windows.Freezable>功能，请参阅[Freezable 对象概述](../advanced/freezable-objects-overview.md)。  
  
-   在中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，不能声明为事件处理程序<xref:System.Windows.Media.Animation.Storyboard>或动画事件。  
  
 有关演示如何定义中的将情节提要的示例<xref:System.Windows.Controls.ControlTemplate>，请参阅[在 ControlTemplate 中的进行动画处理](how-to-animate-in-a-controltemplate.md)示例。  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>在属性值更改时进行动画处理  
 在样式和控件模板中，当属性更改时，可以使用 Trigger 对象来启动情节提要。 有关示例，请参阅[触发动画时在属性值更改](how-to-trigger-an-animation-when-a-property-value-changes.md)并[在 ControlTemplate 中的进行动画处理](how-to-animate-in-a-controltemplate.md)。  
  
 应用属性的动画<xref:System.Windows.Trigger>对象的行为以更复杂的方式比<xref:System.Windows.EventTrigger>动画开始使用<xref:System.Windows.Media.Animation.Storyboard>方法。  在"切换"时使用动画定义由其他<xref:System.Windows.Trigger>对象，但是在编写使用<xref:System.Windows.EventTrigger>和方法触发的动画。  
  
## <a name="see-also"></a>请参阅

- [动画概述](animation-overview.md)
- [属性动画技术概述](property-animation-techniques-overview.md)
- [Freezable 对象概述](../advanced/freezable-objects-overview.md)
