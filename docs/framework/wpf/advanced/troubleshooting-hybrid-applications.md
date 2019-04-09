---
title: 混合应用程序疑难解答
ms.date: 03/30/2017
helpviewer_keywords:
- overlapping controls [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid applications [WPF interoperability]
- message loops [WPF]
ms.assetid: f440c23f-fa5d-4d5a-852f-ba61150e6405
ms.openlocfilehash: 707e77ac69878c1c7fb8e975c1f90ad657228d1a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079665"
---
# <a name="troubleshooting-hybrid-applications"></a>混合应用程序疑难解答
<a name="introduction"></a>本主题列出了在创作同时使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]技术的混合应用程序时可能发生的一些常见问题。  

<a name="overlapping_controls"></a>   
## <a name="overlapping-controls"></a>重叠控件  
 控件可能不按预期的方式重叠。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 为每个控件使用单独的 HWND。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 在页面上的所有内容使用一个 HWND。 这一实现差异会导致意外的重叠行为。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中承载的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件总是出现在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内容之上。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内容中托管<xref:System.Windows.Forms.Integration.ElementHost>控件显示在 z 顺序<xref:System.Windows.Forms.Integration.ElementHost>控件。 可以重叠<xref:System.Windows.Forms.Integration.ElementHost>控件，但所承载[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内容不会组合或交互。  
  
<a name="child_property"></a>   
## <a name="child-property"></a>子属性  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>类只能承载单个子控件或元素。 若要承载多个控件或元素，则必须使用容器作为子内容。 例如，可以添加[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]按钮和复选框控件<xref:System.Windows.Forms.Panel?displayProperty=nameWithType>控件，然后再将分配到面板<xref:System.Windows.Forms.Integration.WindowsFormsHost>控件的<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A>属性。 但是，您不能按钮和复选框控件将分别添加到相同<xref:System.Windows.Forms.Integration.WindowsFormsHost>控件。  
  
<a name="scaling"></a>   
## <a name="scaling"></a>缩放  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]具有不同的缩放模型。 某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 缩放变换对于 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件是有意义的，但其他变换是无意义的。 例如，将 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件缩放到 0 是可行的，但如果尝试将同一控件重新缩放回非零值，该控件的大小仍然为 0。 有关详细信息，请参阅 [WindowsFormsHost 元素的布局注意事项](layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="adapter"></a>   
## <a name="adapter"></a>适配器  
 处理时可能会发生混乱<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>类，因为它们包含一个隐藏的容器。 同时<xref:System.Windows.Forms.Integration.WindowsFormsHost>并<xref:System.Windows.Forms.Integration.ElementHost>类具有名为的隐藏的容器*适配器*，它用来托管内容。 有关<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，该适配器派生<xref:System.Windows.Forms.ContainerControl?displayProperty=nameWithType>类。 有关<xref:System.Windows.Forms.Integration.ElementHost>控件，该适配器派生<xref:System.Windows.Controls.DockPanel>元素。 如果你发现其他互操作主题中提到了适配器，那么所讨论的就是此容器。  
  
<a name="nesting"></a>   
## <a name="nesting"></a>嵌套  
 嵌套<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素内的<xref:System.Windows.Forms.Integration.ElementHost>控件不支持。 嵌套<xref:System.Windows.Forms.Integration.ElementHost>控件内部<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素也不支持。  
  
<a name="focus"></a>   
## <a name="focus"></a>焦点  
 焦点在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]中的工作方式是不同的，这意味着混合应用程序中可能发生焦点问题。 例如，如果内部具有焦点<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，并且你可以最小化和还原页面或显示模式对话框，重点放在<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素可能会丢失。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素仍具有焦点，但其内部的控件可能不会。  
  
 焦点还会影响数据验证。 验证适用于<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，但它不能按你按 tab 键离开<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，或两个不同<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素。  
  
<a name="property_mapping"></a>   
## <a name="property-mapping"></a>属性映射  
 某些属性映射需要先进行大量的转译，才能将 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]技术之间不同的实现桥接起来。 属性映射可使代码对字体、颜色和其他属性的更改做出反应。 通常，属性映射的工作方式是侦听 *Property*Changed 事件或 On*Property* 调用，然后在子控件或其适配器上设置适当的属性。 有关详细信息，请参阅 [Windows 窗体和 WPF 属性映射](windows-forms-and-wpf-property-mapping.md)。  
  
<a name="layoutrelated_properties_on_hosted_content"></a>   
## <a name="layout-related-properties-on-hosted-content"></a>所承载内容上的布局相关属性  
 当<xref:System.Windows.Forms.Integration.WindowsFormsHost.Child%2A?displayProperty=nameWithType>或<xref:System.Windows.Forms.Integration.ElementHost.Child%2A?displayProperty=nameWithType>分配属性，将自动设置所承载内容上的多个布局相关属性。 更改这些内容属性可能会导致意外的布局行为。  
  
 停靠所承载的内容来填充<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>父级。 为了启用此填充行为，在设置子属性时，将设置多个属性。 下表列出了由设置内容属性<xref:System.Windows.Forms.Integration.ElementHost>和<xref:System.Windows.Forms.Integration.WindowsFormsHost>类。  
  
|宿主类|内容属性|  
|----------------|------------------------|  
|<xref:System.Windows.Forms.Integration.ElementHost>|<xref:System.Windows.FrameworkElement.Height%2A><br /><br /> <xref:System.Windows.FrameworkElement.Width%2A><br /><br /> <xref:System.Windows.FrameworkElement.Margin%2A><br /><br /> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A><br /><br /> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|<xref:System.Windows.Forms.Control.Margin%2A><br /><br /> <xref:System.Windows.Forms.Control.Dock%2A><br /><br /> <xref:System.Windows.Forms.Control.AutoSize%2A><br /><br /> <xref:System.Windows.Forms.Control.Location%2A><br /><br /> <xref:System.Windows.Forms.Control.MaximumSize%2A>|  
  
 请勿在所承载的内容上直接设置这些属性。 有关详细信息，请参阅 [WindowsFormsHost 元素的布局注意事项](layout-considerations-for-the-windowsformshost-element.md)。  
  
<a name="navigation_applications"></a>   
## <a name="navigation-applications"></a>导航应用程序  
 导航应用程序不能保持用户状态。 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素导航应用程序中使用时重新创建其控件。 当用户导航操作离开承载的页面重新创建子控件时发生<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素，然后又返回到它。 用户已经键入的所有内容都将丢失。  
  
<a name="message_loop_interoperation"></a>   
## <a name="message-loop-interoperation"></a>消息循环互操作  
 在使用 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]消息循环时，可能无法按照预期方式处理消息。 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>方法由调用<xref:System.Windows.Forms.Integration.WindowsFormsHost>构造函数。 此方法将向 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 消息循环中添加消息筛选器。 此筛选器会调用<xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>方法如果<xref:System.Windows.Forms.Control?displayProperty=nameWithType>是消息的目标和转换/调度该消息。  
  
 如果显示<xref:System.Windows.Window>中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]具有消息循环<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>，您不能键入任何内容，除非调用<xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>方法。 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>方法采用<xref:System.Windows.Window>，并添加<xref:System.Windows.Forms.IMessageFilter?displayProperty=nameWithType>，其中修复重新路由到与键相关的消息[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]消息循环。 有关详细信息，请参阅 [Windows 窗体和 WPF 互操作性输入体系结构](windows-forms-and-wpf-interoperability-input-architecture.md)。  
  
<a name="opacity_and_layering"></a>   
## <a name="opacity-and-layering"></a>不透明度和分层  
 <xref:System.Windows.Interop.HwndHost>类不支持分层。 这意味着该设置<xref:System.Windows.UIElement.Opacity%2A>上的属性<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素不起作用，并且没有值混合处理会与其他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]窗口产生<xref:System.Windows.Window.AllowsTransparency%2A>设置为`true`。  
  
<a name="dispose"></a>   
## <a name="dispose"></a>释放  
 未正确释放类可能会泄漏资源。 在混合应用程序，请确保<xref:System.Windows.Forms.Integration.WindowsFormsHost>和<xref:System.Windows.Forms.Integration.ElementHost>释放类，或可能会泄漏资源。 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] 释放<xref:System.Windows.Forms.Integration.ElementHost>控制其非模式<xref:System.Windows.Forms.Form>父级关闭。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 释放<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素时关闭应用程序。 可以显示<xref:System.Windows.Forms.Integration.WindowsFormsHost>中的元素<xref:System.Windows.Window>中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]消息循环。 在这种情况下，代码可能不会收到应用程序正在关闭的通知。  
  
<a name="enabling_visual_styles"></a>   
## <a name="enabling-visual-styles"></a>启用视觉样式  
 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 视觉样式上[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件可能不会启用。 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>方法调用的模板中[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]应用程序。 尽管默认情况下不会调用此方法，但如果使用 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 创建项目，并且 Comctl32.dll 版本 6.0 可用，将会获得控件的 [!INCLUDE[TLA#tla_winxp](../../../../includes/tlasharptla-winxp-md.md)] 视觉样式。 必须调用<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>方法之前在线程上创建句柄。 有关详细信息，请参阅[如何：混合应用程序中启用视觉样式](how-to-enable-visual-styles-in-a-hybrid-application.md)。  
  
<a name="licensed_controls"></a>   
## <a name="licensed-controls"></a>授权控件  
 授权的 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件会在消息框中向用户显示许可信息，对于混合应用程序，这可能会导致意外行为。 某些授权控件会显示一个对话框来响应创建句柄的操作。 例如，授权控件可能会通知用户需要许可证，或者用户还可以试用该控件三次。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>元素派生自<xref:System.Windows.Interop.HwndHost>内创建类和子控件的句柄<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>方法。 <xref:System.Windows.Interop.HwndHost>类不允许在处理消息<xref:System.Windows.Forms.Integration.WindowsFormsHost.BuildWindowCore%2A>方法，但显示对话框会导致消息发送。 若要启用此许可方案，请调用<xref:System.Windows.Forms.Control.CreateControl%2A?displayProperty=nameWithType>方法之前将其作为分配在控件上的<xref:System.Windows.Forms.Integration.WindowsFormsHost>元素的子级。  
  
<a name="wpf_designer"></a>   
## <a name="wpf-designer"></a>WPF 设计器  
 可以使用 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 设计你的 WPF 内容。 以下部分列出了在使用 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 创作混合应用程序时可能发生的一些常见问题。  
  
### <a name="backcolortransparent-is-ignored-at-design-time"></a>在设计时忽略 BackColorTransparent  
 <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>按预期方式在设计时属性可能无法工作。  
  
 如果 WPF 控件不可见的父级上，WPF 运行时将忽略<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>值。 原因，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>可能会忽略其原因在于<xref:System.Windows.Forms.Integration.ElementHost>中单独创建对象时<xref:System.AppDomain>。 但是，当运行该应用程序，<xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A>按预期方式工作原理。  
  
### <a name="design-time-error-list-appears-when-the-obj-folder-is-deleted"></a>删除 obj 文件夹时出现设计时错误列表  
 如果删除 obj 文件夹，会出现设计时错误列表。  
  
 当您使用设计时<xref:System.Windows.Forms.Integration.ElementHost>，Windows 窗体设计器使用您的项目的 obj 文件夹内 Debug 或 Release 文件夹中生成的文件。 如果删除这些文件，将出现设计时错误列表。 若要解决此问题，请重新生成项目。 有关详细信息，请参阅 [Windows 窗体设计器中的设计时错误](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)。  
  
<a name="elementhost_and_ime"></a>   
## <a name="elementhost-and-ime"></a>ElementHost 和 IME  
 WPF 控件中托管<xref:System.Windows.Forms.Integration.ElementHost>目前不支持<xref:System.Windows.Forms.Control.ImeMode%2A>属性。 将更改为<xref:System.Windows.Forms.Control.ImeMode%2A>所承载的控件将被忽略。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [在 WPF 设计器中的互操作性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628658(v=vs.100))
- [Windows 窗体和 WPF 互操作性输入体系结构](windows-forms-and-wpf-interoperability-input-architecture.md)
- [如何：在混合应用程序中启用视觉对象样式](how-to-enable-visual-styles-in-a-hybrid-application.md)
- [WindowsFormsHost 元素的布局注意事项](layout-considerations-for-the-windowsformshost-element.md)
- [Windows 窗体和 WPF 属性映射](windows-forms-and-wpf-property-mapping.md)
- [Windows 窗体设计器中的设计时错误](../../winforms/controls/design-time-errors-in-the-windows-forms-designer.md)
- [迁移和互操作性](migration-and-interoperability.md)
