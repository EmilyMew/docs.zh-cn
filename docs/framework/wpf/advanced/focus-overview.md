---
title: 焦点概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 72b866d714e6a77020bdb74843c3aaa0ba0c3278
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073879"
---
# <a name="focus-overview"></a>焦点概述
在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，有两个与焦点有关的主要概念：键盘焦点和逻辑焦点。  键盘焦点指接收键盘输入的元素，而逻辑焦点指焦点范围中具有焦点的元素。  本概述详细介绍了这些概念。  对于创建具有多个可获取焦点的区域的复杂应用程序来说，理解这些概念之间的区别非常重要。  
  
 参与焦点管理的主要类是<xref:System.Windows.Input.Keyboard>类，<xref:System.Windows.Input.FocusManager>类和基元素类，如<xref:System.Windows.UIElement>和<xref:System.Windows.ContentElement>。  有关基元素的详细信息，请参阅[基元素概述](base-elements-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard>类而言主要与键盘焦点和<xref:System.Windows.Input.FocusManager>是主要关注逻辑焦点，但这不是一个绝对区别。  具有键盘焦点的元素也具有逻辑焦点，但具有逻辑焦点的元素不一定具有键盘焦点。  当你使用时，这是明显<xref:System.Windows.Input.Keyboard>类来设置为其具有键盘焦点的元素还在元素上设置逻辑焦点。  

<a name="Keyboard_Focus"></a>   
## <a name="keyboard-focus"></a>键盘焦点  
 键盘焦点指当前正在接收键盘输入的元素。  在整个桌面上，只能有一个具有键盘焦点的元素。  在中[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]，具有键盘焦点的元素将具有<xref:System.Windows.IInputElement.IsKeyboardFocused%2A>设置为`true`。  静态属性<xref:System.Windows.Input.Keyboard.FocusedElement%2A>上<xref:System.Windows.Input.Keyboard>类获取当前具有键盘焦点的元素。  
  
 为了使元素能够获取键盘焦点<xref:System.Windows.UIElement.Focusable%2A>并<xref:System.Windows.UIElement.IsVisible%2A>基元素上的属性必须设置为`true`。  一些类，如<xref:System.Windows.Controls.Panel>基类，具有<xref:System.Windows.UIElement.Focusable%2A>设置为`false`默认情况下; 因此，您必须设置<xref:System.Windows.UIElement.Focusable%2A>到`true`如果希望此类元素能够获取键盘焦点。  
  
 可通过用户与 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 交互（例如，按 Tab 键导航到某个元素或者在某些元素上单击鼠标）来获取键盘焦点。  键盘焦点还可以获取以编程方式通过使用<xref:System.Windows.Input.Keyboard.Focus%2A>方法<xref:System.Windows.Input.Keyboard>类。  <xref:System.Windows.Input.Keyboard.Focus%2A>方法尝试将指定的元素的键盘焦点给予。  返回的元素是具有键盘焦点的元素，如果旧的或新的焦点对象阻止请求，则具有键盘焦点的元素可能不是请求的元素。  
  
 下面的示例使用<xref:System.Windows.Input.Keyboard.Focus%2A>方法上设置键盘焦点<xref:System.Windows.Controls.Button>。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>基元素类上的属性获取一个值，该值指示元素是否具有键盘焦点。  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>基元素类上的属性获取一个值，该值指示元素或其任何一个视觉子元素是否具有键盘焦点。  
  
 在设置初始焦点在应用程序启动时，应用程序，加载的初始窗口的可视化树中必须是要接收焦点的元素和元素必须具有<xref:System.Windows.UIElement.Focusable%2A>并<xref:System.Windows.UIElement.IsVisible%2A>设置为`true`。  若要设置初始焦点的建议的位置是在<xref:System.Windows.FrameworkElement.Loaded>事件处理程序。  一个<xref:System.Windows.Threading.Dispatcher>还可以通过调用使用回叫<xref:System.Windows.Threading.Dispatcher.Invoke%2A>或<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>。  
  
<a name="Logical_Focus"></a>   
## <a name="logical-focus"></a>逻辑焦点  
 逻辑焦点指<xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType>焦点范围中。  焦点范围是一个元素，用于跟踪<xref:System.Windows.Input.FocusManager.FocusedElement%2A>其作用域内。  键盘焦点离开焦点范围时，焦点元素会失去键盘焦点，但保留逻辑焦点。  键盘焦点返回到焦点范围时，焦点元素会再次获得键盘焦点。  这使得键盘焦点可在多个焦点范围之间切换，但确保了焦点返回到焦点范围时，焦点范围中的焦点元素重新获得键盘焦点。  
  
 一个应用程序中可以有多个具有逻辑焦点的元素，但在一个特定的焦点范围中只能有一个具有逻辑焦点的元素。  
  
 具有键盘焦点的元素还具有其所属焦点范围的逻辑焦点。  
  
 元素可以转换为中的焦点范围[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]通过设置<xref:System.Windows.Input.FocusManager>附加属性<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>到`true`。  在代码中，元素可以打开转变为焦点范围通过调用<xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A>。  
  
 以下示例使<xref:System.Windows.Controls.StackPanel>转变为焦点范围，通过设置<xref:System.Windows.Input.FocusManager.IsFocusScope%2A>附加属性。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A> 返回指定元素的焦点范围。  
  
 中的类[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]为焦点范围的默认值是<xref:System.Windows.Window>， <xref:System.Windows.Controls.MenuItem>， <xref:System.Windows.Controls.ToolBar>，和<xref:System.Windows.Controls.ContextMenu>。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A> 获取指定的焦点范围内具有焦点的元素。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 在指定的焦点范围内设置具有焦点的元素。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A> 通常用于设置初始焦点的元素。  
  
 以下示例在焦点范围上设置焦点元素并获取焦点范围的焦点元素。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>   
## <a name="keyboard-navigation"></a>键盘导航  
 <xref:System.Windows.Input.KeyboardNavigation>类负责实现默认键盘焦点导航时按下导航键之一。  导航键包括：选项卡、 SHIFT + TAB、 CTRL + TAB、 CTRL + SHIFT + TAB、 向上键、 向下键、 向左键和向右键密钥。  
  
 可以通过设置附加更改导航容器的导航行为<xref:System.Windows.Input.KeyboardNavigation>属性<xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>， <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A>，和<xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A>。  这些属性属于类型<xref:System.Windows.Input.KeyboardNavigationMode>和可能的值为<xref:System.Windows.Input.KeyboardNavigationMode.Continue>， <xref:System.Windows.Input.KeyboardNavigationMode.Local>， <xref:System.Windows.Input.KeyboardNavigationMode.Contained>， <xref:System.Windows.Input.KeyboardNavigationMode.Cycle>， <xref:System.Windows.Input.KeyboardNavigationMode.Once>，和<xref:System.Windows.Input.KeyboardNavigationMode.None>。  默认值是<xref:System.Windows.Input.KeyboardNavigationMode.Continue>，这意味着元素不是导航容器。  
  
 下面的示例创建<xref:System.Windows.Controls.Menu>了大量的<xref:System.Windows.Controls.MenuItem>对象。  <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A>附加的属性设置为<xref:System.Windows.Input.KeyboardNavigationMode.Cycle>上<xref:System.Windows.Controls.Menu>。  使用 tab 键在改变焦点时<xref:System.Windows.Controls.Menu>，焦点将从每个元素和到达最后一个元素时，焦点将返回第一个元素。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>   
## <a name="navigating-focus-programmatically"></a>以编程方式导航焦点  
 其他[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]才能使用焦点会<xref:System.Windows.UIElement.MoveFocus%2A>和<xref:System.Windows.UIElement.PredictFocus%2A>。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A> 将焦点移至应用程序中的下一个元素。  一个<xref:System.Windows.Input.TraversalRequest>使用指定的方向。   <xref:System.Windows.Input.FocusNavigationDirection>传递给<xref:System.Windows.UIElement.MoveFocus%2A>指定不同的方向焦点可以移动，例如<xref:System.Windows.Input.FocusNavigationDirection.First>， <xref:System.Windows.Input.FocusNavigationDirection.Last>，<xref:System.Windows.Input.FocusNavigationDirection.Up>和<xref:System.Windows.Input.FocusNavigationDirection.Down>。  
  
 下面的示例使用<xref:System.Windows.FrameworkElement.MoveFocus%2A>若要更改具有焦点的元素。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A> 返回对象，将焦点更改时接收焦点。  目前，仅<xref:System.Windows.Input.FocusNavigationDirection.Up>， <xref:System.Windows.Input.FocusNavigationDirection.Down>， <xref:System.Windows.Input.FocusNavigationDirection.Left>，和<xref:System.Windows.Input.FocusNavigationDirection.Right>受<xref:System.Windows.FrameworkElement.PredictFocus%2A>。  
  
<a name="Focus_Events"></a>   
## <a name="focus-events"></a>焦点事件  
 与键盘焦点相关的事件都<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>，<xref:System.Windows.Input.Keyboard.GotKeyboardFocus>并<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus>， <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>。  事件定义为附加事件上<xref:System.Windows.Input.Keyboard>类，但作为基元素类上的等效路由事件可更轻松地访问。  有关事件的详细信息，请参阅[路由事件概述](routed-events-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> 该元素获取键盘焦点时引发。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> 元素失去键盘焦点时引发。  如果<xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus>事件或<xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent>处理事件并<xref:System.Windows.RoutedEventArgs.Handled%2A>设置为`true`，则焦点不会更改。  
  
 下面的示例将附加<xref:System.Windows.UIElement.GotKeyboardFocus>并<xref:System.Windows.UIElement.LostKeyboardFocus>的事件处理程序<xref:System.Windows.Controls.TextBox>。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 当<xref:System.Windows.Controls.TextBox>获取键盘焦点<xref:System.Windows.Controls.Control.Background%2A>的属性<xref:System.Windows.Controls.TextBox>更改为<xref:System.Windows.Media.Brushes.LightBlue%2A>。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 当<xref:System.Windows.Controls.TextBox>失去键盘焦点<xref:System.Windows.Controls.Control.Background%2A>属性的<xref:System.Windows.Controls.TextBox>更改回 white。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 与逻辑焦点相关的事件都<xref:System.Windows.UIElement.GotFocus>和<xref:System.Windows.UIElement.LostFocus>。  这些事件定义上<xref:System.Windows.Input.FocusManager>为附加事件，但<xref:System.Windows.Input.FocusManager>不公开 CLR 事件包装器。  <xref:System.Windows.UIElement> 和<xref:System.Windows.ContentElement>更方便地公开这些事件。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [输入概述](input-overview.md)
- [基元素概述](base-elements-overview.md)
