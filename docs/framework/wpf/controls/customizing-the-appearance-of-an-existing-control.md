---
title: 通过创建 ControlTemplate 自定义现有控件的外观
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
ms.openlocfilehash: 5d4b16721dd8cabc5d662538274dcb82ab734cca
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375098"
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>通过创建 ControlTemplate 自定义现有控件的外观
<a name="introduction"></a><xref:System.Windows.Controls.ControlTemplate> 指定视觉结构和控件的视觉行为。 可以通过向控件提供一个新的<xref:System.Windows.Controls.ControlTemplate> 对控件外观进行自定义。 创建 <xref:System.Windows.Controls.ControlTemplate> 时，仅替换现有控件的外观，而不会更改其功能。 例如，可在应用程序中将按钮设置为圆形而不是默认的方形，但按钮仍将引发 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。  
  
 本主题介绍的各个组成部分<xref:System.Windows.Controls.ControlTemplate>，演示如何创建一个简单<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.Button>，并说明如何了解控件的控件协定，使你可以自定义其外观。 因为您创建<xref:System.Windows.Controls.ControlTemplate>在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，可以无需编写任何代码更改控件的外观。 还可以使用设计器（如 Microsoft Expression Blend）创建自定义控件模板。 本主题演示了在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]的自定义的外观<xref:System.Windows.Controls.Button>并列出了本主题末尾的完整示例。 有关使用 Expression Blend 的详细信息，请参阅[设置支持模板的控件的样式](https://go.microsoft.com/fwlink/?LinkId=161153)。  
  
 如下图所示<xref:System.Windows.Controls.Button>，它使用<xref:System.Windows.Controls.ControlTemplate>本主题中创建的。  
  
 ![一个具有自定义控件模板的按钮。](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
使用自定义控件模板的按钮  
  
 ![一个具有红色边框的按钮。](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
使用自定义控件模板并将鼠标指针悬停在上方的按钮  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>系统必备  
 本主题假设用户了解如何创建和使用[控件](index.md)中讨论的控件和样式。 本主题中讨论的概念适用于从继承元素<xref:System.Windows.Controls.Control>类，除<xref:System.Windows.Controls.UserControl>。 无法应用<xref:System.Windows.Controls.ControlTemplate>到<xref:System.Windows.Controls.UserControl>。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>何时应创建 ControlTemplate  
 控件具有许多属性，如<xref:System.Windows.Controls.Border.Background%2A>， <xref:System.Windows.Controls.Control.Foreground%2A>，和<xref:System.Windows.Controls.Control.FontFamily%2A>，可以设置为指定控件的外观的不同方面，但可以通过设置这些属性进行的更改受到限制。 例如，可以设置<xref:System.Windows.Controls.Control.Foreground%2A>属性为蓝色并<xref:System.Windows.Controls.Control.FontStyle%2A>为倾斜<xref:System.Windows.Controls.CheckBox>。  
  
 而无需创建一个新的功能<xref:System.Windows.Controls.ControlTemplate>控件中的所有控件中每个[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-基于应用程序将具有相同的常规外观，这将限制应用程序创建具有自定义外观的功能。 默认情况下，每个<xref:System.Windows.Controls.CheckBox>具有类似的特征。 例如，内容<xref:System.Windows.Controls.CheckBox>始终是位于选择指示器，右侧，总是使用复选标记以指示<xref:System.Windows.Controls.CheckBox>处于选中状态。  
  
 创建<xref:System.Windows.Controls.ControlTemplate>时想要自定义控件的外观之外哪些控件上设置其他属性将执行操作。 在示例中的<xref:System.Windows.Controls.CheckBox>，假设你想要选择指示器上方的复选框的内容以及你希望的 X 指示<xref:System.Windows.Controls.CheckBox>处于选中状态。 指定在这些更改<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.CheckBox>。  
  
 如下图所示<xref:System.Windows.Controls.CheckBox>使用的默认值<xref:System.Windows.Controls.ControlTemplate>。  
  
 ![一个具有默认控件模板的复选框。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
一个具有默认控件模板的复选框  
  
 如下图所示<xref:System.Windows.Controls.CheckBox>使用自定义<xref:System.Windows.Controls.ControlTemplate>的内容放置<xref:System.Windows.Controls.CheckBox>显示 X 选择指示器上方时<xref:System.Windows.Controls.CheckBox>处于选中状态。  
  
 ![一个具有自定义控件模板的复选框。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
一个具有自定义控件模板的复选框  
  
 <xref:System.Windows.Controls.ControlTemplate>有关<xref:System.Windows.Controls.CheckBox>在此示例是相对复杂，因此本主题使用简单的示例演示创建<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.Button>。  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>更改控件的可视结构  
 在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，控件通常是一个复合<xref:System.Windows.FrameworkElement>对象。 当您创建<xref:System.Windows.Controls.ControlTemplate>，你将结合<xref:System.Windows.FrameworkElement>对象以生成单个控件。 一个<xref:System.Windows.Controls.ControlTemplate>必须只有一个<xref:System.Windows.FrameworkElement>作为其根元素。 根元素通常包含其他<xref:System.Windows.FrameworkElement>对象。 对象组合构成控件的可视结构。  
  
 下面的示例创建一个自定义<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.Button>。 <xref:System.Windows.Controls.ControlTemplate>创建的可视结构<xref:System.Windows.Controls.Button>。 在按钮上方移动鼠标指针或单击它时，此示例不会更改按钮的外观。 本主题后面部分将讨论当按钮处于其他状态时更改它的外观。  
  
 在本示例中，可视结构包括以下部分：  
  
-   一个<xref:System.Windows.Controls.Border>名为`RootElement`可用作模板的根<xref:System.Windows.FrameworkElement>。  
  
-   一个<xref:System.Windows.Controls.Grid>的子`RootElement`。  
  
-   一个<xref:System.Windows.Controls.ContentPresenter>显示按钮的内容。 <xref:System.Windows.Controls.ContentPresenter>使任何类型的对象显示。  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>使用 TemplateBinding 保留控件属性的功能  
 当您创建一个新<xref:System.Windows.Controls.ControlTemplate>，您仍可能想要使用的公共属性来更改控件的外观。 [TemplateBinding](../advanced/templatebinding-markup-extension.md)标记扩展将绑定中的元素的属性<xref:System.Windows.Controls.ControlTemplate>到由控件定义的公共属性。 使用 [TemplateBinding](../advanced/templatebinding-markup-extension.md) 时，可让控件属性用作模板参数。 换言之，设置控件属性后，该值将传递到包含 [TemplateBinding](../advanced/templatebinding-markup-extension.md) 的元素。  
  
 下面的示例重复使用前面示例的一部分[TemplateBinding](../advanced/templatebinding-markup-extension.md)绑定中的元素的属性的标记扩展<xref:System.Windows.Controls.ControlTemplate>到按钮定义的公共属性。  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 在此示例中，<xref:System.Windows.Controls.Grid>具有其<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>属性模板绑定到<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>。 因为<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>是模板绑定，可以创建使用相同的多个按钮<xref:System.Windows.Controls.ControlTemplate>并设置<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>为每个按钮上不同的值。 如果<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>未通过模板绑定到中的元素的属性<xref:System.Windows.Controls.ControlTemplate>，并设置<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>某个按钮没有任何影响上按钮的外观。  
  
 请注意，两个属性的名称不必一样。 在前面的示例中，<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>的属性<xref:System.Windows.Controls.Button>模板绑定到<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>属性的<xref:System.Windows.Controls.ContentPresenter>。 这样可以水平放置按钮的内容。 <xref:System.Windows.Controls.ContentPresenter> 不具有名为的属性`HorizontalContentAlignment`，但<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>可以绑定到<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>。 在通过模板绑定属性时，请确保目标属性和源属性属于同一类型。  
  
 <xref:System.Windows.Controls.Control>类定义控件模板必须用于在设置完成后会影响在控件上的多个属性。 如何将<xref:System.Windows.Controls.ControlTemplate>属性依赖于属性的使用。 <xref:System.Windows.Controls.ControlTemplate>必须通过以下方式之一使用属性：  
  
-   中的某个元素<xref:System.Windows.Controls.ControlTemplate>模板绑定到属性。  
  
-   中的元素<xref:System.Windows.Controls.ControlTemplate>从父项继承属性<xref:System.Windows.FrameworkElement>。  
  
 下表列出了由从控件继承的可视属性<xref:System.Windows.Controls.Control>类。 它还指示控件的默认控件模板是使用继承的属性值，还是必须通过模板绑定。  
  
|属性|使用方法|  
|--------------|------------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|模板绑定|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|模板绑定|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|模板绑定|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|属性继承或模板绑定|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|属性继承或模板绑定|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|属性继承或模板绑定|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|属性继承或模板绑定|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|属性继承或模板绑定|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|模板绑定|  
|<xref:System.Windows.Controls.Control.Padding%2A>|模板绑定|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|模板绑定|  
  
 表列出了仅从继承的可视属性<xref:System.Windows.Controls.Control>类。 除了表中列出的属性，该控件还可能会继承<xref:System.Windows.FrameworkElement.DataContext%2A>， <xref:System.Windows.FrameworkElement.Language%2A>，和<xref:System.Windows.Controls.TextBlock.TextDecorations%2A>从父框架元素的属性。  
  
 此外，如果<xref:System.Windows.Controls.ContentPresenter>处于<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.ContentControl>，则<xref:System.Windows.Controls.ContentPresenter>将自动绑定到<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>和<xref:System.Windows.Controls.ContentControl.Content%2A>属性。 同样，<xref:System.Windows.Controls.ItemsPresenter>所在的域<xref:System.Windows.Controls.ControlTemplate>的<xref:System.Windows.Controls.ItemsControl>将自动绑定到<xref:System.Windows.Controls.ItemsControl.Items%2A>和<xref:System.Windows.Controls.ItemsPresenter>属性。  
  
 下面的示例创建两个按钮，它们使用<xref:System.Windows.Controls.ControlTemplate>中前面的示例中定义。 该示例设置<xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.Foreground%2A>，和<xref:System.Windows.Controls.Control.FontSize%2A>上每个按钮的属性。 设置<xref:System.Windows.Controls.Control.Background%2A>属性才有效，因为它是中通过模板绑定<xref:System.Windows.Controls.ControlTemplate>。 即使<xref:System.Windows.Controls.Control.Foreground%2A>和<xref:System.Windows.Controls.Control.FontSize%2A>属性不是模板绑定，将它们设置起作用，因为它们的值继承。  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 前面的示例生成类似于下图的输出。  
  
 ![两个按钮、 一个蓝色和一个紫色。](./media/ndp-buttontwo.png "NDP_ButtonTwo")  
背景色不同的两个按钮  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>根据控件状态更改它的外观  
 显示默认外观的按钮与前面示例中按钮的差异在于，默认按钮在处于不同状态时会略有变化。 例如，在按下按钮或鼠标指针悬停在它的上方时，默认按钮的外观将发生变化。 尽管<xref:System.Windows.Controls.ControlTemplate>不更改的功能的一个控件，它会更改控件的可视行为。 可视行为描述控件处于某种状态下的外观。 若要了解控件功能和可视行为之间的差异，请考虑按钮示例。 按钮的功能是引发<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件时单击它时，但按钮的可视行为是在指向或按下时更改其外观。  
  
 您使用<xref:System.Windows.VisualState>对象处于特定状态时指定控件的外观。 一个<xref:System.Windows.VisualState>包含<xref:System.Windows.Media.Animation.Storyboard>更改中的元素的外观<xref:System.Windows.Controls.ControlTemplate>。 不需要编写任何代码即可使它发生，因为控件逻辑使用更改状态<xref:System.Windows.VisualStateManager>。 在控制进入由指定的状态<xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType>属性，<xref:System.Windows.Media.Animation.Storyboard>开始。 当控件退出该状态，<xref:System.Windows.Media.Animation.Storyboard>停止。  
  
 下面的示例演示<xref:System.Windows.VisualState>更改的外观<xref:System.Windows.Controls.Button>当鼠标指针位于其上方。 <xref:System.Windows.Media.Animation.Storyboard>通过更改的颜色更改按钮的边框颜色`BorderBrush`。 如果您参考<xref:System.Windows.Controls.ControlTemplate>示例在本主题开始时，将会记得`BorderBrush`的名称<xref:System.Windows.Media.SolidColorBrush>分配给<xref:System.Windows.Controls.Border.Background%2A>的<xref:System.Windows.Controls.Border>。  
  
 [!code-xaml[VSMButtonTemplate#4](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 该控件负责将各种状态定义为控件协定的一部分，这将在本主题后面的[通过了解控件协定自定义其他控件](#customizing_other_controls_by_understanding_the_control_contract)中进行详细讨论。 下表列出了为指定的状态<xref:System.Windows.Controls.Button>。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|----------------------|---------------------------|-----------------|  
|普通|CommonStates|默认状态。|  
|MouseOver|CommonStates|鼠标指针悬停在控件上方。|  
|已按下|CommonStates|已按下控件。|  
|已禁用|CommonStates|已禁用控件。|  
|已设定焦点|FocusStates|控件有焦点。|  
|失去焦点|FocusStates|控件没有焦点。|  
  
 <xref:System.Windows.Controls.Button>定义两个状态组：`CommonStates`组中包含`Normal`， `MouseOver`， `Pressed`，并`Disabled`状态。 `FocusStates` 组包含 `Focused` 和 `Unfocused` 状态。 同一状态组中的状态之间相互排斥。 控件在每个组中始终处于一种状态下。 例如，<xref:System.Windows.Controls.Button>可以具有焦点的鼠标指针不是通过它，因此，即使<xref:System.Windows.Controls.Button>中`Focused`状态可以采用`MouseOver`， `Pressed`，或`Normal`状态。  
  
 您将添加<xref:System.Windows.VisualState>对象添加到<xref:System.Windows.VisualStateGroup>对象。 您将添加<xref:System.Windows.VisualStateGroup>对象添加到<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加属性。 下面的示例定义<xref:System.Windows.VisualState>对象的`Normal`， `MouseOver`，和`Pressed`状态，都在`CommonStates`组。 <xref:System.Windows.VisualState.Name%2A>每个<xref:System.Windows.VisualState>与上表中的名称匹配。 省略 `Disabled` 状态和 `FocusStates` 组中的各种状态是为了使示例保持简短，但本主题末尾的完整示例将它们包括在内。  
  
> [!NOTE]
>  请务必设置<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加属性的根<xref:System.Windows.FrameworkElement>的<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 前面的示例生成类似于下图的输出。  
  
 ![一个具有自定义控件模板的按钮。](./media/ndp-buttonnormal.png "NDP_ButtonNormal")  
使用正常状态下的自定义控件模板的按钮  
  
 ![一个具有红色边框的按钮。](./media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
使用鼠标悬停状态下的自定义控件模板的按钮  
  
 ![此边框是透明的按下的按钮。](./media/ndp-buttonpressed.png "NDP_ButtonPressed")  
使用按下状态下的自定义控件模板的按钮  
  
 若要查找附带在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的控件的可视状态，请参阅 [Control 样式和模板](control-styles-and-templates.md)。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>指定控件在状态之间转换时的行为  
 在前面的示例中，按钮的外观在用户单击它时也会发生更改，但除非按钮按下整整一秒，否则用户将看不到效果。 默认情况下，动画需要一秒才会发生。 用户是单击并释放按钮的时间少得多，因为可视反馈将不会生效，如果将<xref:System.Windows.Controls.ControlTemplate>为默认状态。  
  
 您可以指定发生平滑地通过添加转换从一个状态到另一个控制动画所需的时间量<xref:System.Windows.VisualTransition>对象添加到<xref:System.Windows.Controls.ControlTemplate>。 当你创建<xref:System.Windows.VisualTransition>，指定一个或多项操作：  
  
-   在状态之间进行转换所需的时间。  
  
-   在转换的同时，控件外观发生的其他更改。  
  
-   哪些状态<xref:System.Windows.VisualTransition>应用于。  
  
### <a name="specifying-the-duration-of-a-transition"></a>指定转换的持续时间  
 您可以指定多长时间转换所需的设置<xref:System.Windows.VisualTransition.GeneratedDuration%2A>属性。 前面的示例包含<xref:System.Windows.VisualState>，它指定按钮的边框在时按下按钮时，但动画时间太长而引起注意，如果快速按下并释放按钮将变为透明。 可以使用<xref:System.Windows.VisualTransition>若要指定的时间花费在控件转换为按下状态。 以下示例指定控件需要百分之一秒进入按下状态。  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>指定转换时控件外观发生的更改  
 <xref:System.Windows.VisualTransition>包含<xref:System.Windows.Media.Animation.Storyboard>控件状态之间转换时的开始。 例如，可以指定控件从 `MouseOver` 状态转换到 `Normal` 状态时发生的某个动画。 下面的示例创建<xref:System.Windows.VisualTransition>，它指定，当用户移动鼠标指针从按钮，按钮边框更改为蓝色，则为黄色，则为黑色 1.5 秒。  
  
 [!code-xaml[VSMButtonTemplate#8](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>指定何时应用 VisualTransition  
 一个<xref:System.Windows.VisualTransition>可限制要应用于仅某些状态，或可以应用任何时候，只要状态之间的控制转换。 在前面的示例中，<xref:System.Windows.VisualTransition>时在控件转换从应用`MouseOver`状态变为`Normal`状态; 在该示例之前，<xref:System.Windows.VisualTransition>时在控件转换为应用`Pressed`状态。 限制何时<xref:System.Windows.VisualTransition>应用设置<xref:System.Windows.VisualTransition.To%2A>和<xref:System.Windows.VisualTransition.From%2A>属性。 下表描述了从最严限制到最宽松限制的限制级别。  
  
|限制类型|起始值|目标值|  
|-------------------------|-------------------|-----------------|  
|从一个指定状态到另一个指定状态|名称 <xref:System.Windows.VisualState>|名称 <xref:System.Windows.VisualState>|  
|从任意状态到指定状态|未设置|名称 <xref:System.Windows.VisualState>|  
|从指定状态到任意状态|名称 <xref:System.Windows.VisualState>|未设置|  
|从任意状态到其他任意状态|未设置|未设置|  
  
 可以有多个<xref:System.Windows.VisualTransition>中的对象<xref:System.Windows.VisualStateGroup>的引用相同的状态，但它们将使用上一个表指定的顺序。 在以下示例中，有两个<xref:System.Windows.VisualTransition>对象。 该控件时从过渡`Pressed`状态变为`MouseOver`状态，<xref:System.Windows.VisualTransition>同时具有<xref:System.Windows.VisualTransition.From%2A>和<xref:System.Windows.VisualTransition.To%2A>使用集。 当控件从非 `Pressed` 的状态转换为 `MouseOver` 状态时，将使用另一种状态。  
  
 [!code-xaml[VSMButtonTemplate#7](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup>已<xref:System.Windows.VisualStateGroup.Transitions%2A>属性，其中包含<xref:System.Windows.VisualTransition>适用于对象<xref:System.Windows.VisualState>中的对象<xref:System.Windows.VisualStateGroup>。 作为<xref:System.Windows.Controls.ControlTemplate>名作者，你可以自由地包括任何<xref:System.Windows.VisualTransition>想。 但是，如果<xref:System.Windows.VisualTransition.To%2A>并<xref:System.Windows.VisualTransition.From%2A>属性设置为不在的州名<xref:System.Windows.VisualStateGroup>，则<xref:System.Windows.VisualTransition>将被忽略。  
  
 下面的示例演示<xref:System.Windows.VisualStateGroup>为`CommonStates`。 该示例定义了<xref:System.Windows.VisualTransition>为每个按钮的下列转换。  
  
-   转换为 `Pressed` 状态。  
  
-   转换为 `MouseOver` 状态。  
  
-   从 `Pressed` 状态转换为 `MouseOver` 状态。  
  
-   从 `MouseOver` 状态转换为 `Normal` 状态。  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>通过了解控件协定自定义其他控件  
 使用的控件<xref:System.Windows.Controls.ControlTemplate>来指定其可视结构 (通过使用<xref:System.Windows.FrameworkElement>对象) 和可视行为 (通过使用<xref:System.Windows.VisualState>对象) 使用部件控件模型。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 附带的许多控件均使用此模型。 部件的<xref:System.Windows.Controls.ControlTemplate>作者需要注意的通过控件协定。 了解控件协定的各个部件后，可以自定义使用部件控件模型的任意控件的外观。  
  
 控件协定具有三个元素：  
  
-   控件逻辑使用的可视元素。  
  
-   控件状态和每种状态所属的组。  
  
-   以可视方式影响控件的公共属性。  
  
### <a name="visual-elements-in-the-control-contract"></a>控件协定中的可视元素  
 控件的逻辑与的交互有时<xref:System.Windows.FrameworkElement>所在的域<xref:System.Windows.Controls.ControlTemplate>。 例如，控件可能会处理它的其中一个元素的事件。 当控件希望查找特定<xref:System.Windows.FrameworkElement>中<xref:System.Windows.Controls.ControlTemplate>，它必须该信息传达给<xref:System.Windows.Controls.ControlTemplate>作者。 该控件使用<xref:System.Windows.TemplatePartAttribute>要传达的预期，元素和元素的名称应为类型。 <xref:System.Windows.Controls.Button>不具有<xref:System.Windows.FrameworkElement>部件在它的控件协定，但其他控件，如<xref:System.Windows.Controls.ComboBox>，执行操作。  
  
 下面的示例演示<xref:System.Windows.TemplatePartAttribute>指定的对象<xref:System.Windows.Controls.ComboBox>类。 逻辑<xref:System.Windows.Controls.ComboBox>期望找到<xref:System.Windows.Controls.TextBox>名为`PART_EditableTextBox`和一个<xref:System.Windows.Controls.Primitives.Popup>名为`PART_Popup`中其<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 下面的示例演示一个简单<xref:System.Windows.Controls.ControlTemplate>有关<xref:System.Windows.Controls.ComboBox>包含由指定的元素<xref:System.Windows.TemplatePartAttribute>对象上<xref:System.Windows.Controls.ComboBox>类。  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>控件协定中的状态  
 控件状态也属于控件协定。 创建的示例<xref:System.Windows.Controls.ControlTemplate>有关<xref:System.Windows.Controls.Button>演示如何指定的外观<xref:System.Windows.Controls.Button>具体取决于其状态。 您创建<xref:System.Windows.VisualState>为每个指定的状态并使所有<xref:System.Windows.VisualState>对象的共享<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A>中<xref:System.Windows.VisualStateGroup>，如中所述[更改其状态根据控件的外观](#changing_the_appearance_of_a_control_depending_on_its_state)前面的这本主题。 第三方控件应使用指定状态<xref:System.Windows.TemplateVisualStateAttribute>，这样设计器工具，例如 Expression Blend，以公开控件的状态以创作控件模板。  
  
 若要查找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中随附的控件的控件协定，请参阅 [Control 样式和模板](control-styles-and-templates.md)。  
  
### <a name="properties-in-the-control-contract"></a>控件协定中的属性  
 以可视方式影响控件的公共属性也包含在控件协定中。 可以设置这些属性来更改控件的外观，而无需创建一个新<xref:System.Windows.Controls.ControlTemplate>。 此外可以使用[TemplateBinding](../advanced/templatebinding-markup-extension.md)绑定中的元素的属性的标记扩展<xref:System.Windows.Controls.ControlTemplate>到由定义的公共属性<xref:System.Windows.Controls.Button>。  
  
 以下示例展示了按钮的控件协定。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 创建时<xref:System.Windows.Controls.ControlTemplate>，它通常是最简单的方法开始与某个现有<xref:System.Windows.Controls.ControlTemplate>并对其进行更改。 可以执行下列任一操作，更改现有<xref:System.Windows.Controls.ControlTemplate>:  
  
-   使用设计器（例如 Expression Blend），它可以提供用于创建控件模板的图形用户界面。 有关详细信息，请参阅[设置支持模板的控件的样式](https://go.microsoft.com/fwlink/?LinkId=161153)。  
  
-   获取默认<xref:System.Windows.Controls.ControlTemplate>和对其进行编辑。 若要查找 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 随附的默认控件模板，请参阅[默认 WPF 主题](https://go.microsoft.com/fwlink/?LinkID=158252)。  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>完整的示例  
 下面的示例演示的完整<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate>本主题中讨论。  
  
 [!code-xaml[VSMButtonTemplate#3](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>请参阅
- [样式设置和模板化](styling-and-templating.md)
