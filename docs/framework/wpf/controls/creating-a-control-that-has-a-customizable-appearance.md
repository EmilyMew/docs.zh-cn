---
title: 创建具有可自定义外观的控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: 17b6fd604b5eca54d6323701dafdd38f9f6e7328
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131010"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>创建具有可自定义外观的控件
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 使您能够创建可自定义其外观的控件。 例如，可以更改的外观<xref:System.Windows.Controls.CheckBox>超越设置属性即可通过创建一个新<xref:System.Windows.Controls.ControlTemplate>。 如下图所示<xref:System.Windows.Controls.CheckBox>使用的默认值<xref:System.Windows.Controls.ControlTemplate>和一个<xref:System.Windows.Controls.CheckBox>使用自定义<xref:System.Windows.Controls.ControlTemplate>。  
  
 ![一个具有默认控件模板的复选框。](./media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
一个具有默认控件模板的复选框  
  
 ![一个具有自定义控件模板的复选框。](./media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
一个具有自定义控件模板的复选框  
  
 如果您遵循部件和状态模型时创建的控件，，将可自定义控件的外观。 如 Microsoft Expression Blend 设计器工具支持的部件和状态的模型，因此您的控件时请遵循此模型将是可自定义这些类型的应用程序中。  本主题讨论的部件和状态的模型以及如何创建自己的控件时遵循它。 本主题使用的自定义控件示例`NumericUpDown`，来说明此模型的基本原理。  `NumericUpDown`控件中显示数字值，用户可以增加或减少，方法是单击该控件的按钮上显示。  下图显示`NumericUpDown`本主题中讨论的控件。  
  
 ![NumericUpDown 自定义控件。](./media/ndp-numericupdown.png "NDP_NumericUPDown")  
自定义的 NumericUpDown 控件  
  
 本主题包含以下各节：  
  
-   [系统必备](#prerequisites)  
  
-   [部件和状态模型](#parts_and_states_model)  
  
-   [在 ControlTemplate 中定义的可视结构和控件的可视行为](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [使用在代码中的 ControlTemplate 部件](#using_parts_of_the_controltemplate_in_code)  
  
-   [提供控件协定](#providing_the_control_contract)  
  
-   [完整的示例](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>系统必备  
 本主题假定你知道如何创建一个新<xref:System.Windows.Controls.ControlTemplate>为现有控件，使用者熟悉控件协定上的元素是什么，并了解中讨论的概念[自定义现有控件的外观创建 ControlTemplate](customizing-the-appearance-of-an-existing-control.md)。  
  
> [!NOTE]
>  若要创建可以具有自定义其外观的控件，必须创建继承的控件<xref:System.Windows.Controls.Control>类或它的某个子类以外的其他<xref:System.Windows.Controls.UserControl>。  继承的控件<xref:System.Windows.Controls.UserControl>是一个控件，可以快速创建，但它不使用<xref:System.Windows.Controls.ControlTemplate>和不能自定义其外观。  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>部件和状态模型  
 部件和状态模型指定如何定义可视结构和控件的可视行为。 若要遵循的部件和状态的模型，应执行以下操作：  
  
-   定义可视结构和可视行为<xref:System.Windows.Controls.ControlTemplate>的控件。  
  
-   控件的逻辑与控件模板部件的交互时，请遵循一些最佳实践方法。  
  
-   提供用于指定中应包含的内容的控件协定<xref:System.Windows.Controls.ControlTemplate>。  
  
 当定义可视结构和可视行为<xref:System.Windows.Controls.ControlTemplate>控件的应用程序作者可以更改的可视结构和控件的可视行为通过创建一个新<xref:System.Windows.Controls.ControlTemplate>而不是编写代码。   必须提供控件协定，以告知应用程序作者这<xref:System.Windows.FrameworkElement>应中定义的对象和状态<xref:System.Windows.Controls.ControlTemplate>。 中的部件进行交互时，应遵循一些最佳实践<xref:System.Windows.Controls.ControlTemplate>，以便您的控件正确处理不完整<xref:System.Windows.Controls.ControlTemplate>。  如果您遵循这三个原则，将能够创建应用程序作者<xref:System.Windows.Controls.ControlTemplate>控件只是因为它们轻松可以控件的附带[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  以下部分介绍每个这些建议详细信息。  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>在 ControlTemplate 中定义的可视结构和控件的可视行为  
 当使用部件和状态模型创建自定义控件时，您定义控件的可视结构和可视行为及其<xref:System.Windows.Controls.ControlTemplate>而不是其逻辑中。  控件的可视结构是复合形式<xref:System.Windows.FrameworkElement>构成控件的对象。  可视行为是处于特定状态时显示该控件的方法。   有关创建的详细信息<xref:System.Windows.Controls.ControlTemplate>，用于指定可视结构和控件的可视行为，请参阅[通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)。  
  
 在示例中的`NumericUpDown`控件的可视结构包含两个<xref:System.Windows.Controls.Primitives.RepeatButton>控件和一个<xref:System.Windows.Controls.TextBlock>。  如果您的代码中添加这些控件`NumericUpDown`管理-在其构造函数，例如，这些控件的位置将无法更改。  而不是在其代码中定义控件的可视结构和可视行为，应将其定义中<xref:System.Windows.Controls.ControlTemplate>。  然后应用程序开发人员自定义按钮的位置和<xref:System.Windows.Controls.TextBlock>并指定所发生的行为时`Value`为负因为<xref:System.Windows.Controls.ControlTemplate>可替换。  
  
 下面的示例演示的可视结构`NumericUpDown`控件，其中包括<xref:System.Windows.Controls.Primitives.RepeatButton>增加`Value`、 一个<xref:System.Windows.Controls.Primitives.RepeatButton>减少`Value`，和一个<xref:System.Windows.Controls.TextBlock>以显示`Value`。  
  
 [!code-xaml[VSMCustomControl#VisualStructure](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 可视行为`NumericUpDown`控件是如果它为负的值是以红色字体。  如果您更改<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>时在代码中`Value`为负，`NumericUpDown`将始终显示为红色的负值。 指定在控件的可视行为<xref:System.Windows.Controls.ControlTemplate>加上<xref:System.Windows.VisualState>对象添加到<xref:System.Windows.Controls.ControlTemplate>。  下面的示例演示<xref:System.Windows.VisualState>对象的`Positive`和`Negative`状态。  `Positive` 并`Negative`是互斥的 （控件将始终处于其中的两个），因此示例将放<xref:System.Windows.VisualState>成了一个对象<xref:System.Windows.VisualStateGroup>。  在控件转换为`Negative`状态，<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>将变为红色。  当控件处于`Positive`状态，<xref:System.Windows.Controls.TextBlock.Foreground%2A>返回到其原始值。  定义<xref:System.Windows.VisualState>中的对象<xref:System.Windows.Controls.ControlTemplate>中进一步讨论[通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)。  
  
> [!NOTE]
>  请务必设置<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加属性的根<xref:System.Windows.FrameworkElement>的<xref:System.Windows.Controls.ControlTemplate>。  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>使用在代码中的 ControlTemplate 部件  
 一个<xref:System.Windows.Controls.ControlTemplate>作者可能会省略<xref:System.Windows.FrameworkElement>或<xref:System.Windows.VisualState>对象，有意或意外，但控件的逻辑可能需要这些部件能够正常工作。 部件和状态模型指定控件应该能够应对<xref:System.Windows.Controls.ControlTemplate>缺少<xref:System.Windows.FrameworkElement>或<xref:System.Windows.VisualState>对象。  您的控件不应引发异常或报表错误如果<xref:System.Windows.FrameworkElement>， <xref:System.Windows.VisualState>，或<xref:System.Windows.VisualStateGroup>缺少<xref:System.Windows.Controls.ControlTemplate>。 本部分介绍用于与进行交互的建议的做法<xref:System.Windows.FrameworkElement>对象，并管理状态。  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>预计缺少 FrameworkElement 对象  
 在定义<xref:System.Windows.FrameworkElement>中的对象<xref:System.Windows.Controls.ControlTemplate>，控件的逻辑可能需要与其中一些交互。  例如，`NumericUpDown`按钮的控件订阅<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件来增加或减少`Value`，并设置<xref:System.Windows.Controls.TextBlock.Text%2A>属性<xref:System.Windows.Controls.TextBlock>到`Value`。 如果自定义<xref:System.Windows.Controls.ControlTemplate>省略<xref:System.Windows.Controls.TextBlock>或者按钮，它是可接受在控件失去其部分功能，但您应确保您的控件不会导致错误。 例如，如果<xref:System.Windows.Controls.ControlTemplate>不包含要更改的按钮`Value`，则`NumericUpDown`，该功能，但使用的应用程序将失去<xref:System.Windows.Controls.ControlTemplate>将继续运行。  
  
 以下做法可确保控件正确响应与缺少<xref:System.Windows.FrameworkElement>对象：  
  
1.  设置`x:Name`为每个属性<xref:System.Windows.FrameworkElement>，您需要在代码中引用。  
  
2.  为每个定义私有属性<xref:System.Windows.FrameworkElement>需要与之交互。  
  
3.  订阅和取消订阅您的控件以处理任何事件<xref:System.Windows.FrameworkElement>属性的 set 访问器。  
  
4.  设置<xref:System.Windows.FrameworkElement>中定义的属性中的步骤 2<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>方法。 这是最早的<xref:System.Windows.FrameworkElement>在<xref:System.Windows.Controls.ControlTemplate>可供该控件。 使用`x:Name`的<xref:System.Windows.FrameworkElement>若要从中获取此<xref:System.Windows.Controls.ControlTemplate>。  
  
5.  检查<xref:System.Windows.FrameworkElement>不是`null`之前访问其成员。  如果它是`null`，不报告错误。  
  
 下面的示例演示如何`NumericUpDown`控件与交互<xref:System.Windows.FrameworkElement>根据前面的列表中建议的对象。  
  
 在以下示例中定义的可视结构`NumericUpDown`控制<xref:System.Windows.Controls.ControlTemplate>，则<xref:System.Windows.Controls.Primitives.RepeatButton>增加`Value`具有其`x:Name`属性设置为`UpButton`。  下面的示例声明一个名为属性`UpButtonElement`，表示<xref:System.Windows.Controls.Primitives.RepeatButton>中声明的<xref:System.Windows.Controls.ControlTemplate>。 `set`访问器首先取消到按钮的<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件如果`UpDownElement`不是`null`，然后设置该属性，然后它订阅<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。 此外，还有属性定义，但不是能为另，如下所示<xref:System.Windows.Controls.Primitives.RepeatButton>，称为`DownButtonElement`。  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 下面的示例演示<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>为`NumericUpDown`控件。  该示例使用<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>方法以获取<xref:System.Windows.FrameworkElement>对象从<xref:System.Windows.Controls.ControlTemplate>。  请注意，此示例可防止针对事例<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>查找<xref:System.Windows.FrameworkElement>具有指定名称，并且不属于预期类型。 它也是一种最佳的做法，忽略具有指定的元素`x:Name`但属于错误的类型。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 按照前面的示例中所示的做法，确保您的控件将继续运行时<xref:System.Windows.Controls.ControlTemplate>缺少<xref:System.Windows.FrameworkElement>。  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>使用 VisualStateManager 来管理状态  
 <xref:System.Windows.VisualStateManager>跟踪控件状态以及执行状态间转换所需的逻辑。 当您将添加<xref:System.Windows.VisualState>对象添加到<xref:System.Windows.Controls.ControlTemplate>，你将其添加到<xref:System.Windows.VisualStateGroup>并添加<xref:System.Windows.VisualStateGroup>到<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>附加属性，以便<xref:System.Windows.VisualStateManager>有权访问它们。  
  
 下面的示例重复前面的示例表明<xref:System.Windows.VisualState>对应于对象`Positive`和`Negative`控件的状态。 <xref:System.Windows.Media.Animation.Storyboard>中`Negative`<xref:System.Windows.VisualState>变为<xref:System.Windows.Controls.TextBlock.Foreground%2A>的<xref:System.Windows.Controls.TextBlock>红色。   当`NumericUpDown`控件处于`Negative`状态，则在情节提要`Negative`状态开始。  然后<xref:System.Windows.Media.Animation.Storyboard>中`Negative`当控件返回到状态停止`Positive`状态。  `Positive`<xref:System.Windows.VisualState>不需要包含<xref:System.Windows.Media.Animation.Storyboard>因为时<xref:System.Windows.Media.Animation.Storyboard>有关`Negative`停止，<xref:System.Windows.Controls.TextBlock.Foreground%2A>返回到其原始的颜色。  
  
 [!code-xaml[VSMCustomControl#ValueStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 请注意，<xref:System.Windows.Controls.TextBlock>被赋予一个名称，但<xref:System.Windows.Controls.TextBlock>中的控件协定不是`NumericUpDown`因为永远不会引用控件的逻辑<xref:System.Windows.Controls.TextBlock>。  在中引用的元素<xref:System.Windows.Controls.ControlTemplate>具有的名称，但不是需要将其控件协定的一部分，因为新<xref:System.Windows.Controls.ControlTemplate>对于控件可能不需要引用该元素。  例如，创建一个新的人<xref:System.Windows.Controls.ControlTemplate>有关`NumericUpDown`可能会决定不指示`Value`通过更改为负<xref:System.Windows.Controls.Control.Foreground%2A>。  在这种情况下，都不在代码中也不<xref:System.Windows.Controls.ControlTemplate>引用<xref:System.Windows.Controls.TextBlock>按名称。  
  
 控件的逻辑负责更改控件的状态。 下面的示例演示`NumericUpDown`控制调用<xref:System.Windows.VisualStateManager.GoToState%2A>方法进入`Positive`状态时`Value`0 或更高版本，并且`Negative`状态时`Value`小于 0。  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A>方法执行所需启动和停止情节提要适当的逻辑。 当控件调用<xref:System.Windows.VisualStateManager.GoToState%2A>以更改其状态，<xref:System.Windows.VisualStateManager>执行以下操作：  
  
-   如果<xref:System.Windows.VisualState>控件转到具有<xref:System.Windows.Media.Animation.Storyboard>，情节提要开始。 然后，如果<xref:System.Windows.VisualState>来自该控件具有<xref:System.Windows.Media.Animation.Storyboard>，情节提要结束。  
  
-   如果控件已指定，则州<xref:System.Windows.VisualStateManager.GoToState%2A>不执行任何操作，并返回`true`。  
  
-   如果指定的状态中不存在<xref:System.Windows.Controls.ControlTemplate>的`control`，<xref:System.Windows.VisualStateManager.GoToState%2A>不执行任何操作，并返回`false`。  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>使用 VisualStateManager 的最佳实践  
 建议以下操作来维护控件的状态：  
  
-   使用属性来跟踪其状态。  
  
-   创建一个帮助器方法用于状态之间转换。  
  
 `NumericUpDown`控件使用其`Value`属性以跟踪是否正在`Positive`或`Negative`状态。  `NumericUpDown`还定义了控件`Focused`并`UnFocused`指出，哪些跟踪<xref:System.Windows.UIElement.IsFocused%2A>属性。 如果使用不自然地对应于控件的属性的状态，可以定义一个私有属性来跟踪状态。  
  
 更新所有状态的单一方法可集中管理对调用<xref:System.Windows.VisualStateManager>并使代码更易于管理。 下面的示例演示`NumericUpDown`控件的帮助器方法， `UpdateStates`。 当`Value`大于或等于 0，<xref:System.Windows.Controls.Control>处于`Positive`状态。  当`Value`是小于 0，该控件处于`Negative`状态。  当<xref:System.Windows.UIElement.IsFocused%2A>是`true`，在控件处于`Focused`状态，否则为它是在`Unfocused`状态。  该控件可以调用`UpdateStates`每当需要更改其状态，而不考虑所处的状态更改。  
  
 [!code-csharp[VSMCustomControl#UpdateStates](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 如果通过将状态名称传递给<xref:System.Windows.VisualStateManager.GoToState%2A>时该控件已处于该状态<xref:System.Windows.VisualStateManager.GoToState%2A>不执行任何操作，因此无需检查的控件的当前状态。  例如，如果`Value`从一个负号更改为另一个负数的情节提要`Negative`不中断状态，用户不会在控件中的发生更改。  
  
 <xref:System.Windows.VisualStateManager>使用<xref:System.Windows.VisualStateGroup>对象，以确定哪种状态时调用退出<xref:System.Windows.VisualStateManager.GoToState%2A>。 控件将始终处于一个状态为每个<xref:System.Windows.VisualStateGroup>中定义其<xref:System.Windows.Controls.ControlTemplate>，才离开前一种状态时将它放入另一种状态从同一个<xref:System.Windows.VisualStateGroup>。 例如，<xref:System.Windows.Controls.ControlTemplate>的`NumericUpDown`控件定义`Positive`并`Negative`<xref:System.Windows.VisualState>中其中一个对象<xref:System.Windows.VisualStateGroup>并`Focused`和`Unfocused`<xref:System.Windows.VisualState>中另一个对象。 (您所见`Focused`并`Unfocused`<xref:System.Windows.VisualState>中定义[完整示例](#complete_example)当控件从本主题中的部分`Positive`状态变为`Negative`状态，或反之，该控件将保留在要么`Focused`或`Unfocused`状态。  
  
 有以下三个控件的状态可能会更改其中的典型位置：  
  
-   当<xref:System.Windows.Controls.ControlTemplate>应用于<xref:System.Windows.Controls.Control>。  
  
-   当属性更改。  
  
-   在事件发生时。  
  
 以下示例演示了更新的状态`NumericUpDown`在这些情况下的控件。  
  
 应更新中的控件的状态<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>方法，以便正确显示该控件运行时<xref:System.Windows.Controls.ControlTemplate>应用。 下面的示例调用`UpdateStates`在<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>可确保在控件处于相应状态。  例如，假设您创建`NumericUpDown`控件，并将其<xref:System.Windows.Controls.Control.Foreground%2A>为绿色和`Value`-5。  如果不调用`UpdateStates`时<xref:System.Windows.Controls.ControlTemplate>应用于`NumericUpDown`控件，该控件不在`Negative`状态，并且值为绿色而不是红色。  必须调用`UpdateStates`若要将控件放入`Negative`状态。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 通常需要更新控件属性发生更改时的状态。 下面的示例显示了完整`ValueChangedCallback`方法。 因为`ValueChangedCallback`时，将调用`Value`发生更改，方法调用`UpdateStates`以防`Value`更改从正为负，反之亦然。 它是可接受要调用`UpdateStates`时`Value`更改，但仍保持正数或负数，因为在这种情况下，该控件将不会更改状态。  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 您可能还需要更新状态事件发生时。 下面的示例演示`NumericUpDown`调用`UpdateStates`上<xref:System.Windows.Controls.Control>来处理<xref:System.Windows.UIElement.GotFocus>事件。  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager>可帮助您管理您的控件的状态。 通过使用<xref:System.Windows.VisualStateManager>，确保控件正确状态之间转换。  如果您遵循有关使用此部分中所述的建议<xref:System.Windows.VisualStateManager>，控件的代码将保持可读性和可维护性。  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>提供控件协定  
 提供控件协定，以便<xref:System.Windows.Controls.ControlTemplate>作者会知道要放置在模板中的内容。 控件协定具有三个元素：  
  
-   控件逻辑使用的可视元素。  
  
-   控件状态和每种状态所属的组。  
  
-   以可视方式影响控件的公共属性。  
  
 创建一个新的某人<xref:System.Windows.Controls.ControlTemplate>需要知道什么<xref:System.Windows.FrameworkElement>控件的逻辑使用的对象类型的每个对象是和它的名称是。 一个<xref:System.Windows.Controls.ControlTemplate>作者还需要了解的控件可以在中，每个可能的状态和名称<xref:System.Windows.VisualStateGroup>状态为。  
  
 返回到`NumericUpDown`示例中，控件应当<xref:System.Windows.Controls.ControlTemplate>具有以下<xref:System.Windows.FrameworkElement>对象：  
  
-   一个<xref:System.Windows.Controls.Primitives.RepeatButton>调用`UpButton`。  
  
-   一个<xref:System.Windows.Controls.Primitives.RepeatButton>调用 `DownButton.`  
  
 该控件可处于以下状态：  
  
-   在 `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   在 `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 若要指定的内容<xref:System.Windows.FrameworkElement>对象控件预期，则使用<xref:System.Windows.TemplatePartAttribute>，它指定的名称和预期元素的类型。  若要指定一个控件的可能状态，请使用<xref:System.Windows.TemplateVisualStateAttribute>，它指定该状态的名称和其中<xref:System.Windows.VisualStateGroup>它属于。  将放<xref:System.Windows.TemplatePartAttribute>和<xref:System.Windows.TemplateVisualStateAttribute>的类定义中的控件。  
  
 在控件的外观会影响任何公共属性也是控件协定的一部分。  
  
 下面的示例指定<xref:System.Windows.FrameworkElement>对象和状态`NumericUpDown`控件。  
  
 [!code-csharp[VSMCustomControl#ControlContract](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>完整的示例  
 下面的示例是整个<xref:System.Windows.Controls.ControlTemplate>为`NumericUpDown`控件。  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 下面的示例演示的逻辑`NumericUpDown`。  
  
 [!code-csharp[VSMCustomControl#ControlLogic](~/samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](~/samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>请参阅

- [通过创建 ControlTemplate 自定义现有控件的外观](customizing-the-appearance-of-an-existing-control.md)
- [控件自定义](control-customization.md)
