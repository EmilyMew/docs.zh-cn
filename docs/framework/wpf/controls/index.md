---
title: Controls
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: f4aeb3dd60186a4060f7825257c7adb274fc8b24
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363145"
---
# <a name="controls"></a>Controls
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 附带许多中几乎每个 Windows 应用程序中，如使用的常见 UI 组件<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.TextBox>， <xref:System.Windows.Controls.Menu>，和<xref:System.Windows.Controls.ListBox>。 以前，这些对象称为控件。 虽然[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]SDK 继续使用术语"控件"泛指任何代表应用程序中的可见对象的类务必要注意类不需要从继承<xref:System.Windows.Controls.Control>类即可具有可见外观。 继承的类<xref:System.Windows.Controls.Control>类包含<xref:System.Windows.Controls.ControlTemplate>，它允许控件的使用方从根本上更改控件的外观，而无需创建新子类。  本主题讨论如何控件 (那些从继承<xref:System.Windows.Controls.Control>类和一些未) 中常用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>创建控件的实例  
 可以向应用程序添加一个控件，通过使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]或代码。  下面的示例演示如何创建一个向用户询问其姓名的简单应用程序。  此示例创建六个控件： 两个标签、 两个文本框及两个按钮，在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 所有控件均可使用相似方式创建。  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 以下示例在代码中创建相同的应用程序。 为简洁起见，创建<xref:System.Windows.Controls.Grid>， `grid1`，已排除的示例。 `grid1` 具有相同的列和行定义，在前面所示[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]示例。  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>更改控件的外观  
 更改控件的外观以适应应用程序的外观，这是很常见的操作。 可以根据要达到的效果，通过执行以下操作之一来更改控件的外观：  
  
-   更改控件的属性值。  
  
-   创建<xref:System.Windows.Style>控件。  
  
-   创建一个新<xref:System.Windows.Controls.ControlTemplate>控件。  
  
### <a name="changing-a-controls-property-value"></a>更改控件的属性值  
 许多控件具有属性，可用于更改控件的显示方式，如<xref:System.Windows.Controls.Control.Background%2A>的<xref:System.Windows.Controls.Button>。 可以在这种设置的值属性[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]和代码。 下面的示例设置<xref:System.Windows.Controls.Control.Background%2A>， <xref:System.Windows.Controls.Control.FontSize%2A>，并<xref:System.Windows.Controls.Control.FontWeight%2A>上的属性<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 下面的示例在代码中设置相同的属性。  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>为控件创建样式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使您能够指定控件的外观成批，而不是在应用程序中，每个实例上设置属性，通过创建<xref:System.Windows.Style>。 下面的示例创建<xref:System.Windows.Style>应用于每个<xref:System.Windows.Controls.Button>应用程序中。 <xref:System.Windows.Style> 定义通常在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]中<xref:System.Windows.ResourceDictionary>，如<xref:System.Windows.FrameworkElement.Resources%2A>属性的<xref:System.Windows.FrameworkElement>。  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 您可以还样式将仅应用于某些特定类型的通过将键分配给样式并指定该注册表项中的`Style`控件的属性。  有关样式的详细信息，请参阅[样式和模板化](styling-and-templating.md)。  
  
### <a name="creating-a-controltemplate"></a>创建 ControlTemplate  
 一个<xref:System.Windows.Style>允许您一次，多个控件设置属性，但有时您可能想要自定义的外观<xref:System.Windows.Controls.Control>超出如何通过创建<xref:System.Windows.Style>。 继承的类<xref:System.Windows.Controls.Control>类具有<xref:System.Windows.Controls.ControlTemplate>，用于定义的结构和外观<xref:System.Windows.Controls.Control>。 <xref:System.Windows.Controls.Control.Template%2A>的属性<xref:System.Windows.Controls.Control>是公共的所以可以向<xref:System.Windows.Controls.Control><xref:System.Windows.Controls.ControlTemplate>不同于其默认值。 通常可以指定一个新<xref:System.Windows.Controls.ControlTemplate>有关<xref:System.Windows.Controls.Control>而不是从控件的外观进行自定义继承<xref:System.Windows.Controls.Control>。  
  
 请考虑一个很常见的控件， <xref:System.Windows.Controls.Button>。  主要行为<xref:System.Windows.Controls.Button>是为了使应用程序采取某些操作，当用户单击它。  默认情况下<xref:System.Windows.Controls.Button>在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]显示为一个凸出的矩形。  在开发应用程序时，你可能想要充分利用的行为<xref:System.Windows.Controls.Button>-即，通过处理按钮的单击事件，但可能会更改超出你可以通过更改按钮的属性执行的操作的按钮的外观。  在这种情况下，您可以创建一个新<xref:System.Windows.Controls.ControlTemplate>。  
  
 下面的示例创建<xref:System.Windows.Controls.ControlTemplate>为<xref:System.Windows.Controls.Button>。  <xref:System.Windows.Controls.ControlTemplate>创建<xref:System.Windows.Controls.Button>带有圆的角和渐变背景。  <xref:System.Windows.Controls.ControlTemplate>包含<xref:System.Windows.Controls.Border>其<xref:System.Windows.Controls.Border.Background%2A>是<xref:System.Windows.Media.LinearGradientBrush>具有两个<xref:System.Windows.Media.GradientStop>对象。  第一个<xref:System.Windows.Media.GradientStop>使用数据绑定来绑定<xref:System.Windows.Media.GradientStop.Color%2A>属性的<xref:System.Windows.Media.GradientStop>到按钮的背景的颜色。  当您将设置<xref:System.Windows.Controls.Control.Background%2A>的属性<xref:System.Windows.Controls.Button>，该值的颜色将用作第一个<xref:System.Windows.Media.GradientStop>。 有关数据绑定的详细信息，请参阅[数据绑定概述](../data/data-binding-overview.md)。 此示例还创建<xref:System.Windows.Trigger>更改的外观<xref:System.Windows.Controls.Button>时<xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A>是`true`。  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
>  <xref:System.Windows.Controls.Control.Background%2A>的属性<xref:System.Windows.Controls.Button>必须设置为<xref:System.Windows.Media.SolidColorBrush>示例才能正常工作。  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>订阅事件  
 您可以通过使用订阅控件的事件[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]或代码，但您只能处理代码中的事件。  下面的示例演示如何订阅`Click`事件的<xref:System.Windows.Controls.Button>。  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 下面的示例处理`Click`事件的<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>控件中的丰富内容  
 继承的大多数类<xref:System.Windows.Controls.Control>类具有包含丰富内容的能力。 例如，<xref:System.Windows.Controls.Label>可以包含任意对象，一个字符串，例如<xref:System.Windows.Controls.Image>，或<xref:System.Windows.Controls.Panel>。  以下类支持丰富的内容，充当用于在控件中的大部分的基类[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]。  
  
-   <xref:System.Windows.Controls.ContentControl>-从此类继承的类的示例包括<xref:System.Windows.Controls.Label>， <xref:System.Windows.Controls.Button>，和<xref:System.Windows.Controls.ToolTip>。  
  
-   <xref:System.Windows.Controls.ItemsControl>-从此类继承的类的示例包括<xref:System.Windows.Controls.ListBox>， <xref:System.Windows.Controls.Menu>，和<xref:System.Windows.Controls.Primitives.StatusBar>。  
  
-   <xref:System.Windows.Controls.HeaderedContentControl>-从此类继承的类的示例包括<xref:System.Windows.Controls.TabItem>， <xref:System.Windows.Controls.GroupBox>，和<xref:System.Windows.Controls.Expander>。  
  
-   <xref:System.Windows.Controls.HeaderedItemsControl>-从此类继承的类的示例包括<xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.TreeViewItem>，和<xref:System.Windows.Controls.ToolBar>。  

  
 有关这些基类的类的详细信息，请参阅[WPF 内容模型](wpf-content-model.md)。  
  
## <a name="see-also"></a>请参阅
- [样式设置和模板化](styling-and-templating.md)
- [按类别分类的控件](controls-by-category.md)
- [控件库](control-library.md)
- [数据模板化概述](../data/data-templating-overview.md)
- [数据绑定概述](../data/data-binding-overview.md)
- [输入](../advanced/input-wpf.md)
- [启用命令](../advanced/how-to-enable-a-command.md)
- [演练：创建自定义的动画的按钮](walkthroughs-create-a-custom-animated-button.md)
- [控件自定义](control-customization.md)
