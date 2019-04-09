---
title: 样式设置和模板化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- triggers [WPF]
- styles [WPF], referencing
- event triggers [WPF]
- styles [WPF], prerequisites
- styles [WPF], declaring
- styles [WPF], overview
- styles [WPF], extending
- styles [WPF], triggers
- styles [WPF], event triggers
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
ms.openlocfilehash: 3fae4993a13b02ad998668f644a80ba7c07196fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132285"
---
# <a name="styling-and-templating"></a>样式设置和模板化
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 样式和模板化是指一套功能 （样式、 模板、 触发器和情节提要），以允许开发人员和设计人员可以创建极具视觉表现力的效果，以创建一致的外观对其产品。 尽管开发者和/或设计者可以逐个应用程序地广泛自定义外观，但为了实现应用程序内部和之间的外观维护和共享，需要一个强大的样式设置和模板化模型。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了该模型。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 样式设置模型的另一项功能是将演示与逻辑分离。 这意味着，设计者可以仅使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 处理应用程序外观，与此同时开发者使用 C# 或 Visual Basic 处理编程逻辑。  
  
 本概述侧重于应用程序的样式设置和模板化方面，不讨论任何数据绑定概念。 有关数据绑定的信息，请参阅[数据绑定概述](../data/data-binding-overview.md)。  
  
 此外，了解资源很重要，正是这些资源使样式和模板能够重复使用。 有关资源的详细信息，请参阅 [XAML 资源](../advanced/xaml-resources.md)。

<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>样式设置和模板化示例  
 本概述中使用的代码示例基于下图中所示的简单照片示例：  
  
 ![Styled ListView](./media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 此简单照片示例使用样式设置和模板化创建极具视觉表现力的用户体验。 此示例具有两个<xref:System.Windows.Controls.TextBlock>元素和一个<xref:System.Windows.Controls.ListBox>控件绑定到映像的列表。 有关完整示例，请参阅[样式设置和模板化示例简介](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>样式基础知识  
 您可以将<xref:System.Windows.Style>作为方便地将一组属性值应用于多个元素。 例如，请考虑以下<xref:System.Windows.Controls.TextBlock>元素和它们的默认外观：  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![样式设置示例屏幕截图](./media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 您可以通过设置属性，如更改默认外观<xref:System.Windows.Controls.Control.FontSize%2A>并<xref:System.Windows.Controls.Control.FontFamily%2A>，在每个<xref:System.Windows.Controls.TextBlock>直接元素。 但是，如果你想你<xref:System.Windows.Controls.TextBlock>元素共享某些属性，可以创建<xref:System.Windows.Style>中`Resources`一部分您[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件，如下所示：  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 当您将设置<xref:System.Windows.Style.TargetType%2A>的到您的风格<xref:System.Windows.Controls.TextBlock>类型，该样式应用于所有<xref:System.Windows.Controls.TextBlock>窗口中的元素。  
  
 现在<xref:System.Windows.Controls.TextBlock>元素出现，如下所示：  
  
 ![样式设置示例屏幕截图](./media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>扩展样式  
 您可能需要两个<xref:System.Windows.Controls.TextBlock>元素共享某些属性值，如<xref:System.Windows.Controls.Control.FontFamily%2A>和居中<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>，但也希望文本"My Pictures"具有某些其他属性。 可以通过创建基于第一个样式的新样式来实现该目标，如下所示：  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 请注意，上面的样式提供 `x:Key`。 若要应用该样式，您设置<xref:System.Windows.FrameworkElement.Style%2A>属性上的你<xref:System.Windows.Controls.TextBlock>到`x:Key`值，如下所示：  
  
 [!code-xaml[StylingIntroSnippet#UIText](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 这<xref:System.Windows.Controls.TextBlock>样式现在具有<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>的值<xref:System.Windows.HorizontalAlignment.Center>、 一个<xref:System.Windows.Controls.TextBlock.FontFamily%2A>的值`Comic Sans MS`、 一个<xref:System.Windows.Controls.TextBlock.FontSize%2A>值为 26，和一个<xref:System.Windows.Controls.TextBlock.Foreground%2A>值设置为<xref:System.Windows.Media.LinearGradientBrush>示例所示。 请注意，它将替代<xref:System.Windows.Controls.Control.FontSize%2A>的基本样式的值。 如果有多个<xref:System.Windows.Setter>中设置同一属性<xref:System.Windows.Style>，则<xref:System.Windows.Setter>，它是声明最后一个优先。  
  
 下面显示了什么<xref:System.Windows.Controls.TextBlock>元素现在看起来像：  
  
 ![带样式的 TextBlocks](./media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 这`TitleText`样式扩展已为创建的样式<xref:System.Windows.Controls.TextBlock>类型。 还可以使用 `x:Key` 值扩展具有 `x:Key` 的样式。 有关示例，请参阅为提供的示例<xref:System.Windows.Style.BasedOn%2A>属性。  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType 属性和 x:Key 属性之间的关系  
 第一个示例中所示，设置<xref:System.Windows.Style.TargetType%2A>属性设置为`TextBlock`而无需为样式分配`x:Key`会导致该样式应用于所有<xref:System.Windows.Controls.TextBlock>元素。 在此情况下，`x:Key` 隐式设置为 `{x:Type TextBlock}`。 这意味着，如果显式设置`x:Key`值到的任何内容，而`{x:Type TextBlock}`，则<xref:System.Windows.Style>不应用于所有<xref:System.Windows.Controls.TextBlock>元素自动。 相反，必须应用样式 (通过使用`x:Key`值) 到<xref:System.Windows.Controls.TextBlock>元素显式。 如果您的方式是在资源部分中，并且未设置<xref:System.Windows.Style.TargetType%2A>属性上应用样式，则你必须提供`x:Key`。  
  
 除了提供的默认值之外`x:Key`，则<xref:System.Windows.Style.TargetType%2A>属性指定 setter 属性应用的类型。 如果未指定<xref:System.Windows.Style.TargetType%2A>，必须限定的属性中您<xref:System.Windows.Setter>对象使用的语法的类名称与`Property="ClassName.Property"`。 例如，而不是设置`Property="FontSize"`，则必须设置<xref:System.Windows.Setter.Property%2A>到`"TextBlock.FontSize"`或`"Control.FontSize"`。  
  
 另请注意，许多 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控件由其他 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控件的组合构成。 如果创建应用于某个类型的所有控件的样式，可能会产生意外结果。 例如，如果创建一种样式面向<xref:System.Windows.Controls.TextBlock>中键入<xref:System.Windows.Window>，该样式应用到所有<xref:System.Windows.Controls.TextBlock>控件在窗口中，即使<xref:System.Windows.Controls.TextBlock>属于另一个控件，如<xref:System.Windows.Controls.ListBox>。  
  
### <a name="styles-and-resources"></a>样式和资源  
 可以从派生的任何元素上使用样式<xref:System.Windows.FrameworkElement>或<xref:System.Windows.FrameworkContentElement>。 声明样式的最常见方法是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件的 `Resources` 部分中声明为样式，如前面的示例所示。 由于样式是资源，因此它们遵循应用于所有资源的相同范围规则；声明样式的位置影响可应用样式的位置。 例如，如果在应用程序定义 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件的根元素中声明样式，则该样式可以在应用程序中的任何位置使用。 如果创建一个导航应用程序，并在应用程序 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件之一中声明样式，则该样式只能在该 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件中使用。 有关资源的范围规则的详细信息，请参阅 [XAML 资源](../advanced/xaml-resources.md)。  
  
 此外，可以在本概述后面部分的[共享资源和主题](#styling_themes)中找到有关样式和资源的详细信息。  
  
### <a name="setting-styles-programmatically"></a>以编程方式设置样式  
 若要以编程方式将已命名的样式分配到的元素，请从资源集合中获取样式并将其分配给元素的<xref:System.Windows.FrameworkElement.Style%2A>属性。 请注意，资源集合中的项类型的<xref:System.Object>。 因此，您必须强制转换为检索到的样式<xref:System.Windows.Style>之前将其分配给<xref:System.Windows.FrameworkElement.Style%2A>属性。 例如，若要设置已定义`TitleText`上设置样式<xref:System.Windows.Controls.TextBlock>名为`textblock1`，执行以下操作：  
  
 [!code-csharp[StylingIntroSample_snippet#Code](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 请注意，一旦应用样式，它将被密封，并且不能更改。 如果要动态更改已应用的样式，必须创建新的样式来替换现有样式。 有关更多信息，请参见 <xref:System.Windows.Style.IsSealed%2A> 属性。  
  
 可以创建一个根据自定义逻辑选择要应用的样式的对象。 有关示例，请参阅为提供的示例<xref:System.Windows.Controls.StyleSelector>类。  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>绑定、动态资源和事件处理程序  
 请注意，可以使用 `Setter.Value` 属性指定[绑定标记扩展](../advanced/binding-markup-extension.md)或 [DynamicResource 标记扩展](../advanced/dynamicresource-markup-extension.md)。 有关详细信息，请参阅为提供的示例<xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType>属性。  
  
 到目前为止，本概述仅讨论使用资源库设置属性值。 还可以在样式中指定事件处理程序。 有关详细信息，请参阅 <xref:System.Windows.EventSetter>。  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>数据模板  
 在此示例应用程序中，没有<xref:System.Windows.Controls.ListBox>绑定到的照片列表控件：  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 这<xref:System.Windows.Controls.ListBox>目前看起来如下所示：  
  
 ![应用模板之前的 ListBox](./media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 大多数控件都具有某些类型的内容，并且该内容通常来自要绑定到的数据。 在此示例中，数据是照片列表。 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，则使用<xref:System.Windows.DataTemplate>来定义数据的可视化表示形式。 基本上，什么放入<xref:System.Windows.DataTemplate>确定数据在呈现的应用程序中的样子。  
  
 在示例应用程序中，每个自定义 `Photo` 对象都有一个字符串类型的 `Source` 属性，用于指定图像的文件路径。 当前，照片对象显示为文件路径。  
  
 若要显示为图像使照片，您创建<xref:System.Windows.DataTemplate>作为资源：  
  
 [!code-xaml[StylingIntroSnippet#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 请注意，<xref:System.Windows.DataTemplate.DataType%2A>属性是非常类似于<xref:System.Windows.Style.TargetType%2A>属性的<xref:System.Windows.Style>。 如果你<xref:System.Windows.DataTemplate>时，可以在资源部分中，指定<xref:System.Windows.DataTemplate.DataType%2A>属性设置为一种类型并不将其分配`x:Key`，则<xref:System.Windows.DataTemplate>只要该类型将显示应用。 您始终可以选择要将分配<xref:System.Windows.DataTemplate>与`x:Key`，然后将其设置为`StaticResource`采用<xref:System.Windows.DataTemplate>类型，如<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>属性或<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>属性。  
  
 从根本上来说，<xref:System.Windows.DataTemplate>在上面的示例定义每当存在`Photo`对象，它应显示为<xref:System.Windows.Controls.Image>内<xref:System.Windows.Controls.Border>。 与此<xref:System.Windows.DataTemplate>，我们的应用程序现在如下所示：  
  
 ![照片图像](./media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 数据模板化模型提供其他功能。 例如，如果您要显示包含使用其他集合的集合数据<xref:System.Windows.Controls.HeaderedItemsControl>键入类似于<xref:System.Windows.Controls.Menu>或<xref:System.Windows.Controls.TreeView>，没有<xref:System.Windows.HierarchicalDataTemplate>。 另一个数据模板化功能是<xref:System.Windows.Controls.DataTemplateSelector>，可用于选择<xref:System.Windows.DataTemplate>使用根据自定义逻辑。 有关详细信息，请参阅[数据模板化概述](../data/data-templating-overview.md)，该概述提供不同数据模板化功能的更多深入讨论。  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>控件模板  
 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，则<xref:System.Windows.Controls.ControlTemplate>控件的定义控件的外观。 可以通过定义一个新更改的结构和控件的外观<xref:System.Windows.Controls.ControlTemplate>控件。 在许多情况下，这提供了足够的灵活性，从而无需自行编写自定义控件。 有关详细信息，请参阅[通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)。  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Triggers  
 触发器在属性值发生更改或引发事件时设置属性或启动操作，例如动画。 <xref:System.Windows.Style><xref:System.Windows.Controls.ControlTemplate>，并<xref:System.Windows.DataTemplate>所有具有`Triggers`包含一组触发器的属性。 触发器有各种类型。  
  
### <a name="property-triggers"></a>属性触发器  
 一个<xref:System.Windows.Trigger>设置属性值或启动基于属性的值的操作称为属性触发器。  
  
 若要演示如何使用属性触发器，可以将每个<xref:System.Windows.Controls.ListBoxItem>部分透明，除非它被选中。 下面的样式集<xref:System.Windows.UIElement.Opacity%2A>的值<xref:System.Windows.Controls.ListBoxItem>到`0.5`。 当<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>属性是`true`，但<xref:System.Windows.UIElement.Opacity%2A>设置为`1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 此示例使用<xref:System.Windows.Trigger>若要设置的属性值，但请注意<xref:System.Windows.Trigger>类还具有<xref:System.Windows.TriggerBase.EnterActions%2A>和<xref:System.Windows.TriggerBase.ExitActions%2A>启用触发器执行的操作的属性。  
  
 请注意，<xref:System.Windows.FrameworkElement.MaxHeight%2A>的属性<xref:System.Windows.Controls.ListBoxItem>设置为`75`。 在下图中，第三项是选中的项：  
  
 ![Styled ListView](./media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTrigger 和情节提要  
 另一种触发器是<xref:System.Windows.EventTrigger>，从而启动一组基于事件的匹配项的操作。 例如，以下<xref:System.Windows.EventTrigger>对象指定当鼠标指针进入<xref:System.Windows.Controls.ListBoxItem>，则<xref:System.Windows.FrameworkElement.MaxHeight%2A>属性的值进行动画处理`90`转移`0.2`第二个句点。 当鼠标离开该项时，属性在 `1` 秒的时间内返回到原始值。 请注意如何不需要指定<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>值<xref:System.Windows.ContentElement.MouseLeave>动画。 这是因为动画能够跟踪原始值。  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](~/samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 有关详细信息，请参阅[情节提要概述](../graphics-multimedia/storyboards-overview.md)。  
  
 在下图中，鼠标指向第三个项：  
  
 ![样式设置示例屏幕截图](./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTrigger、DataTrigger 和 MultiDataTrigger  
 除了<xref:System.Windows.Trigger>和<xref:System.Windows.EventTrigger>，有其他类型的触发器。 <xref:System.Windows.MultiTrigger> 可以设置基于多个条件的属性值。 您使用<xref:System.Windows.DataTrigger>和<xref:System.Windows.MultiDataTrigger>时您的条件的属性是数据绑定。  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>共享资源和主题  
 典型的 Windows Presentation Foundation (WPF) 应用程序可能具有多个应用于整个应用程序的用户界面 (UI) 资源。 总体上，可以将这组资源视为应用程序的主题。 Windows Presentation Foundation (WPF) 支持打包用户界面 (UI) 资源作为主题通过提供一个资源字典，其中封装为<xref:System.Windows.ResourceDictionary>类。  
  
 Windows Presentation Foundation (WPF) 主题是使用定义的样式设置和模板化机制，Windows Presentation Foundation (WPF) 公开用于自定义视觉对象的所有元素。  
  
 Windows Presentation Foundation (WPF) 主题资源存储在嵌入的资源字典。 这些资源必须嵌入到已签名的程序集内，并且可以嵌入到与代码本身相同的程序集内或并行程序集内。 对于包含 Windows Presentation Foundation (WPF) 控件的程序集 PresentationFramework.dll 主题资源位于一系列通过并行程序集。  
  
 该主题成为在搜索元素样式时最后查看的位置。 通常，搜索先沿着元素树搜索适当的资源，然后在应用程序资源集合中查找，最后查询系统。 这样一来，应用程序开发者便有机会在到达主题之前在树或应用程序级别上为任何对象重新定义样式。  
  
 可以将资源字典定义为个别文件，这些文件支持跨多个应用程序重复使用主题。 还可以通过定义多个资源字典来创建可交换的主题，这些资源字典以不同的值提供相同类型的资源。 在应用程序级别上重新定义这些样式或其他资源是设计应用程序外观的推荐方法。  
  
 若要共享一组资源，包括跨应用程序、 样式和模板，可以创建[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件，并定义<xref:System.Windows.ResourceDictionary>。 例如，看一看下图，它显示[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)的一部分：

![控件模板示例](./media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 如果查看示例中的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 文件，将注意到这些文件都具有以下内容：  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 它是共享`shared.xaml`，用于定义<xref:System.Windows.ResourceDictionary>，其中包含一组样式和画笔资源，使具有一致的外观的示例中的控件。  
  
 有关详细信息，请参阅[合并资源字典](../advanced/merged-resource-dictionaries.md)。  
  
 如果要为自定义控件创建主题，请参阅[控件创作概述](control-authoring-overview.md)的外部控件库部分。  
  
## <a name="see-also"></a>请参阅

- [WPF 中的 Pack URI](../app-development/pack-uris-in-wpf.md)
- [如何：查找由 ControlTemplate 生成的元素](how-to-find-controltemplate-generated-elements.md)
- [查找由 DataTemplate 生成的元素](../data/how-to-find-datatemplate-generated-elements.md)
