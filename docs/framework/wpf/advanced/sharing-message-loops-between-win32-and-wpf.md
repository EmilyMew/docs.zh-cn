---
title: 在 Win32 和 WPF 之间共享消息循环
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 74055ec3facb7db9145c4c0e969d57da24eccbc8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115071"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>在 Win32 和 WPF 之间共享消息循环
本主题介绍如何实现与互操作的消息循环[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]，通过使用现有的消息循环中的进行展示<xref:System.Windows.Threading.Dispatcher>或通过创建单独的消息循环上[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]端的互操作代码。  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher 和消息循环  
 正常情况下，互操作和键盘事件支持的是实现<xref:System.Windows.Interop.IKeyboardInputSink>，或从已实现的类的子类<xref:System.Windows.Interop.IKeyboardInputSink>，如<xref:System.Windows.Interop.HwndSource>或<xref:System.Windows.Interop.HwndHost>。 但是，键盘接收器支持不能解决时发送和接收跨互操作边界的消息可能遇到的所有可能的消息循环需求。 若要帮助形式化应用程序消息循环体系结构，[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供了<xref:System.Windows.Interop.ComponentDispatcher>类，该类定义的消息循环，以按照一个简单的协议。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 是一个静态类，公开多个成员。 每个方法的作用域是隐式绑定到调用线程。 消息循环必须调用其中一些[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]（如在下一节中定义） 的关键时刻。  
  
 <xref:System.Windows.Interop.ComponentDispatcher> 提供的其他组件 （例如键盘接收器中） 可以侦听的事件。 <xref:System.Windows.Threading.Dispatcher>类将调用所有相应<xref:System.Windows.Interop.ComponentDispatcher>相应序列中的方法。 如果要实现您自己的消息循环，你的代码负责调用<xref:System.Windows.Interop.ComponentDispatcher>中类似的方式的方法。  
  
 调用<xref:System.Windows.Interop.ComponentDispatcher>线程上的方法将只会调用该线程注册的事件处理程序。  
  
## <a name="writing-message-loops"></a>编写消息循环  
 下面是清单<xref:System.Windows.Interop.ComponentDispatcher>如果编写您自己的消息循环，则将使用的成员：  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>： 您的消息循环应调用此函数以指示该线程是模式。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>： 您的消息循环应调用此函数以指示该线程已恢复为非模式线程。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>： 您的消息循环应调用此函数以指示<xref:System.Windows.Interop.ComponentDispatcher>应引发<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>事件。 <xref:System.Windows.Interop.ComponentDispatcher> 将不会引发<xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>如果<xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>是`true`，但也可以选择调用消息循环<xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>即使<xref:System.Windows.Interop.ComponentDispatcher>不能对其在模式状态做出响应。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>： 您的消息循环应调用此函数以指示有可用的新消息。 返回值指示是否为侦听器<xref:System.Windows.Interop.ComponentDispatcher>事件处理该消息。 如果<xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>返回`true`（处理），调度程序不执行任何操作进一步并显示消息。 如果返回值是`false`，则调度程序应调用[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]函数`TranslateMessage`，然后调用`DispatchMessage`。  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>使用 ComponentDispatcher 和现有消息处理  
 以下是的清单<xref:System.Windows.Interop.ComponentDispatcher>成员将使用如果依赖于固有[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]消息循环。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>： 返回应用程序是否已进入模式状态 （例如，已推送模式消息循环）。 <xref:System.Windows.Interop.ComponentDispatcher> 可以跟踪此状态，因为此类维护的计数<xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>和<xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>消息循环中的调用。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> 和<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>事件遵循委托调用的标准规则。 委托调用中未指定的顺序，并且所有委托都调用即使第一个会将消息标记为已处理。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>： 表示适当和有效时间执行空闲处理 （没有其他挂起消息的线程）。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> 将不会引发如果线程是模式。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>： 引发的消息泵处理所有消息。  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>： 期间尚未处理的所有消息引发<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>。  
  
 则认为该消息已处理后的，如果<xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>事件或<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>事件，`handled`中的事件数据的引用传递参数是`true`。 事件处理程序应忽略该消息，如果`handled`是`true`，因为这意味着不同的处理程序首先处理该消息。 这两个事件的事件处理程序可能会修改消息。 修改后的消息并不是原始的未更改的消息应调度调度程序。 <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> 传递到所有侦听器，但体系结构的意图是仅包含目标的消息应在其中调用响应消息中的代码的 HWND 的顶级窗口。  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>HwndSource ComponentDispatcher 事件的处理方式  
 如果<xref:System.Windows.Interop.HwndSource>是一个顶级窗口 （没有父项 HWND），它将向注册<xref:System.Windows.Interop.ComponentDispatcher>。 如果<xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>引发时，如果消息适用于<xref:System.Windows.Interop.HwndSource>或子窗口<xref:System.Windows.Interop.HwndSource>调用其<xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>， <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>，<xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A>键盘接收器序列。  
  
 如果<xref:System.Windows.Interop.HwndSource>不是一个顶级窗口 （具有一个父级 HWND），会有任何处理。 只有顶级窗口执行处理，并且存在预期可具有键盘接收器支持的最高级别窗口作为任何互操作方案的一部分。  
  
 如果<xref:System.Windows.Interop.HwndHost.WndProc%2A>上<xref:System.Windows.Interop.HwndSource>称为没有首先调用相应的键盘接收器方法，你的应用程序都将收到更高的级别的键盘事件如<xref:System.Windows.UIElement.KeyDown>。 但是，没有键盘接收器将调用方法，从而避开了所需的键盘输入的模型功能，例如访问密钥支持。 这可能是因为消息循环未正确在通知相关线程<xref:System.Windows.Interop.ComponentDispatcher>，或者是因为父 HWND 未调用相应的键盘接收器响应。  
  
 转到键盘接收器的可能不将消息发送到 HWND 如果挂钩，该消息添加了使用<xref:System.Windows.Interop.HwndSource.AddHook%2A>方法。 该消息可能具有已处理，在直接和未提交到消息泵级别`DispatchMessage`函数。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [WPF 和 Win32 互操作](wpf-and-win32-interoperation.md)
- [线程处理模型](threading-model.md)
- [输入概述](input-overview.md)
