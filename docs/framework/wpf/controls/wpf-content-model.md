---
title: WPF 内容模型
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: 6cbb13fdcba2cf014c4c31a5dc5b21fe2721b214
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816910"
---
# <a name="wpf-content-model"></a>WPF 内容模型
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 是一个演示平台，提供了许多控件和类似控件的类型，主要用于显示不同类型的内容。 若要确定所要使用的控件或要从其派生的控件，应该了解特定控件可以最佳效果显示的对象类型。  
  
 本主题概述了适用于 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控件和类似控件的类型的内容模型。 内容模型描述可在控件中使用的内容。 本主题还列出了每个内容模型的内容属性。 内容属性是一种用于存储对象内容的属性。  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>包含任意内容的类  
 某些控件可以包含的任何类型，如字符串、 对象<xref:System.DateTime>对象，或<xref:System.Windows.UIElement>，它是其他项的容器。 例如，<xref:System.Windows.Controls.Button>可以包含图像和一些文本，或<xref:System.Windows.Controls.CheckBox>可以包含的值<xref:System.DateTime.Now%2A?displayProperty=nameWithType>。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 有四个可包含任意内容的类。 下表列出了继承的类<xref:System.Windows.Controls.Control>。  
  
|包含任意内容的类|内容|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|一个任意对象。|  
|<xref:System.Windows.Controls.HeaderedContentControl>|一个标头和一个项（两者都是任意对象）。|  
|<xref:System.Windows.Controls.ItemsControl>|一个任意对象集合。|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|一个标头和一个项集合（全部都是任意对象）。|  
  
 继承自这些类的控件可以包含相同类型的内容，并可以采用相同方式处理该内容。 下图显示了来自每个内容模型包含图像和一些文本的控件：  
  
 ![显示四个不同的控件，从每个内容模型的屏幕截图。](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>包含一个任意对象的控件  
 <xref:System.Windows.Controls.ContentControl>类包含一段任意内容。 它的内容属性是<xref:System.Windows.Controls.ContentControl.Content%2A>。 以下控件继承自<xref:System.Windows.Controls.ContentControl>并使用其内容模型：  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 下图显示四个按钮，其<xref:System.Windows.Controls.ContentControl.Content%2A>设置为字符串，<xref:System.DateTime>对象， <xref:System.Windows.Shapes.Rectangle>，和一个<xref:System.Windows.Controls.Panel>，其中包含<xref:System.Windows.Shapes.Ellipse>和<xref:System.Windows.Controls.TextBlock>:  
  
 ![显示具有不同内容类型的四个按钮的屏幕截图。](./media/wpf-content-model/control-content-model-buttons.png)  
  
 有关如何设置的示例<xref:System.Windows.Controls.ContentControl.Content%2A>属性，请参阅<xref:System.Windows.Controls.ContentControl>。  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>包含一个标头和一个任意对象的控件  
 <xref:System.Windows.Controls.HeaderedContentControl>类继承自<xref:System.Windows.Controls.ContentControl>并显示一个标头的内容。 它将继承的 content 属性<xref:System.Windows.Controls.ContentControl.Content%2A>，从<xref:System.Windows.Controls.ContentControl>，并定义<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>的类型的属性<xref:System.Object>; 因此，都可以为任意对象。  
  
 以下控件继承自<xref:System.Windows.Controls.HeaderedContentControl>并使用其内容模型：  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 下图显示了两个<xref:System.Windows.Controls.TabItem>对象。 第一个<xref:System.Windows.Controls.TabItem>已<xref:System.Windows.UIElement>对象作为<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和<xref:System.Windows.Controls.ContentControl.Content%2A>。 <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>设置为<xref:System.Windows.Controls.StackPanel>，其中包含<xref:System.Windows.Shapes.Ellipse>和一个<xref:System.Windows.Controls.TextBlock>。 <xref:System.Windows.Controls.ContentControl.Content%2A>设置为<xref:System.Windows.Controls.StackPanel>，其中包含<xref:System.Windows.Controls.TextBlock>和一个<xref:System.Windows.Controls.Label>。 第二个<xref:System.Windows.Controls.TabItem>具有一个字符串<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>和一个<xref:System.Windows.Controls.TextBlock>中<xref:System.Windows.Controls.ContentControl.Content%2A>。  
  
 ![在标头属性中使用不同类型的 TabControl。](./media/wpf-content-model/control-content-model-tab.png)  
  
 有关如何创建的示例<xref:System.Windows.Controls.TabItem>对象，请参阅<xref:System.Windows.Controls.HeaderedContentControl>。  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>包含一个任意对象集合的控件  
 <xref:System.Windows.Controls.ItemsControl>类继承自<xref:System.Windows.Controls.Control>，可以包含多个项，如字符串、 对象或其他元素。 其内容属性为<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>和<xref:System.Windows.Controls.ItemsControl.Items%2A>。 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 通常用于填充<xref:System.Windows.Controls.ItemsControl>与数据收集。 如果您不想要使用集合来填充<xref:System.Windows.Controls.ItemsControl>，可以通过使用添加项<xref:System.Windows.Controls.ItemsControl.Items%2A>属性。  
  
 以下控件继承自<xref:System.Windows.Controls.ItemsControl>并使用其内容模型：  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 下图显示<xref:System.Windows.Controls.ListBox>，其中包含这些类型的项：  
  
-   一个字符串。  
  
-   一个 <xref:System.DateTime> 对象。  
  
-   <xref:System.Windows.UIElement>。  
  
-   一个<xref:System.Windows.Controls.Panel>，其中包含<xref:System.Windows.Shapes.Ellipse>和一个<xref:System.Windows.Controls.TextBlock>。  
  
 ![显示具有四种类型的内容的 ListBox 的屏幕截图。](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>包含一个标头和一个任意对象集合的控件  
 <xref:System.Windows.Controls.HeaderedItemsControl>类继承自<xref:System.Windows.Controls.ItemsControl>，可以包含多个项，如字符串、 对象或其他元素和一个标头。 它将继承<xref:System.Windows.Controls.ItemsControl>内容属性， <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>，并<xref:System.Windows.Controls.ItemsControl.Items%2A>，它定义<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>可以是任意对象的属性。  
  
 以下控件继承自<xref:System.Windows.Controls.HeaderedItemsControl>并使用其内容模型：  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>包含一个 UIElement 对象集合的类  
 <xref:System.Windows.Controls.Panel>类进行定位并排列子<xref:System.Windows.UIElement>对象。 它的内容属性是<xref:System.Windows.Controls.Panel.Children%2A>。  
  
 以下类继承自<xref:System.Windows.Controls.Panel>类并使用其内容模型：  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 有关详细信息，请参阅[面板概述](panels-overview.md)。  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>影响 UIElement 外观的类  
 <xref:System.Windows.Controls.Decorator>类应用视觉效果上或周围单个子<xref:System.Windows.UIElement>。 它的内容属性是<xref:System.Windows.Controls.Decorator.Child%2A>。 以下类继承自<xref:System.Windows.Controls.Decorator>并使用其内容模型：  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 如下图所示<xref:System.Windows.Controls.TextBox>具有 （即装饰有）<xref:System.Windows.Controls.Border>围绕它。  
  
 ![具有黑色边框的 TextBox](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
具有边框的 TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>提供 UIElement 相关视觉反馈的类  
 <xref:System.Windows.Documents.Adorner>类向用户提供可视化提示。 例如，使用<xref:System.Windows.Documents.Adorner>向元素添加功能句柄或提供有关控件的状态信息。 <xref:System.Windows.Documents.Adorner>类提供一个框架，以便您可以创建自己的装饰器。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 不会提供任何实现的装饰器。 有关详细信息，请参阅[装饰器概述](adorners-overview.md)。  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>可让用户输入文本的类  
 WPF 提供了三个可让用户输入文本的主要控件。 每个控件都以不同方式显示文本。 下表列出了这三个与文本相关的控件、显示文本时的功能以及包含控件文本的属性。  
  
|控件|文本显示方式|内容属性|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|纯文本|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|带格式文本|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|隐藏文本（字符已屏蔽）|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>显示文本的类  
 某些类可用于显示纯文本或带格式文本。 可以使用<xref:System.Windows.Controls.TextBlock>显示少量文本。 如果你想要显示大量文本，使用<xref:System.Windows.Controls.FlowDocumentReader>， <xref:System.Windows.Controls.FlowDocumentPageViewer>，或<xref:System.Windows.Controls.FlowDocumentScrollViewer>控件。  
  
 <xref:System.Windows.Controls.TextBlock>具有两个内容属性：<xref:System.Windows.Controls.TextBlock.Text%2A>和<xref:System.Windows.Controls.TextBlock.Inlines%2A>。 如果想要显示使用一致格式的文本<xref:System.Windows.Controls.TextBlock.Text%2A>属性通常是最佳选择。 如果你打算使用不同的格式设置在整个文本，使用<xref:System.Windows.Controls.TextBlock.Inlines%2A>属性。 <xref:System.Windows.Controls.TextBlock.Inlines%2A>属性是一系列<xref:System.Windows.Documents.Inline>对象，指定如何设置文本的格式。  
  
 下表列出的内容属性<xref:System.Windows.Controls.FlowDocumentReader>， <xref:System.Windows.Controls.FlowDocumentPageViewer>，和<xref:System.Windows.Controls.FlowDocumentScrollViewer>类。  
  
|控件|内容属性|内容属性类型|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Document|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Document|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Document|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument>实现<xref:System.Windows.Documents.IDocumentPaginatorSource>接口; 因此，所有三个类，可能需要<xref:System.Windows.Documents.FlowDocument>作为内容。  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>设置文本格式的类  
 <xref:System.Windows.Documents.TextElement> 和及其相关的类可用于设置文本的格式。 <xref:System.Windows.Documents.TextElement> 对象包含和中的文本格式<xref:System.Windows.Controls.TextBlock>和<xref:System.Windows.Documents.FlowDocument>对象。 两种主要类型的<xref:System.Windows.Documents.TextElement>对象是<xref:System.Windows.Documents.Block>元素和<xref:System.Windows.Documents.Inline>元素。 一个<xref:System.Windows.Documents.Block>元素表示的文本，例如段落或列表的块。 <xref:System.Windows.Documents.Inline>元素表示块中的文本的一部分。 许多<xref:System.Windows.Documents.Inline>类指定应用于中文本的格式。 每个<xref:System.Windows.Documents.TextElement>具有其自己的内容模型。 有关详细信息，请参阅 [TextElement 内容模型概述](../advanced/textelement-content-model-overview.md)。  
  
## <a name="see-also"></a>请参阅
- [高级](../advanced/index.md)
