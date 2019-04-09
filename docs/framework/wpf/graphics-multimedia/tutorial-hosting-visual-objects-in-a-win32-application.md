---
title: 教程：在 Win32 应用程序中承载视觉对象
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: b260f96246f0d9e5447b74a05e1396bfef176197
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111457"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>教程：在 Win32 应用程序中承载视觉对象
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供用于创建应用程序的丰富环境。 但是，当您有大量投入时[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]代码中，可能会更有效地添加[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]功能提供给你的应用程序而不是重写代码。 为提供支持[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]和[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]在应用程序，以并发方式使用的图形子系统[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供了用于托管中的对象的机制[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口。  
  
 本教程介绍如何编写示例应用程序，[使用 Win32 互操作示例命中测试](https://go.microsoft.com/fwlink/?LinkID=159995)，则该主机[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]视觉对象中[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口。  

<a name="requirements"></a>   
## <a name="requirements"></a>要求  
 本教程假定你已基本熟悉 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 和 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] 编程。 有关的基本介绍[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]编程，请参见[演练：我第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。 以大致[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]编程，请参见的众多书籍的任何主题，具体而言*编程 Windows* Charles Petzold 的。  
  
> [!NOTE]
>  本教程包括来自相关示例的一些代码示例。 但是，出于可读性考虑，不包括完整的示例代码。 有关完整的示例代码，请参阅[使用 Win32 互操作示例命中测试](https://go.microsoft.com/fwlink/?LinkID=159995)。  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>创建宿主 Win32 窗口  
 托管的关键[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的对象[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口是<xref:System.Windows.Interop.HwndSource>类。 此类将包装[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]中的对象[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口中，从而允许它们合并到您[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]用作子窗口。  
  
 下面的示例演示用于创建的代码<xref:System.Windows.Interop.HwndSource>对象作为[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]视觉对象的容器窗口。 若要设置窗口样式、 位置和其他参数[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口中，使用<xref:System.Windows.Interop.HwndSourceParameters>对象。  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  值<xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A>属性不能设置为 WS_EX_TRANSPARENT。 这意味着，宿主[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口不能为透明。 出于此原因，主机的背景色[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口设置为作为其父窗口相同的背景色。  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>将视觉对象添加到宿主 Win32 窗口  
 当创建了主机后[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]容器窗口中的视觉对象，可以向其添加视觉对象。 你将想要确保诸如动画等视觉对象的任何转换不会超出边界的主机[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口的边框。  
  
 下面的示例演示用于创建代码<xref:System.Windows.Interop.HwndSource>对象，并向其添加视觉对象。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A>的属性<xref:System.Windows.Interop.HwndSource>对象设置为第一个视觉对象添加到主机[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口。 根视觉对象定义视觉对象树最顶层的节点。 任何后续的视觉对象添加到主机[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口添加为子对象。  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>实现 Win32 消息筛选器  
 主机[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]视觉对象的窗口需要窗口消息筛选器过程，以处理从应用程序队列发送到窗口的消息。 窗口过程接收来自消息[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]系统。 这些消息可以是输入消息，也可以是窗口管理消息。 可以选择在窗口过程中处理一条消息，或将消息传递到系统以供默认处理。  
  
 <xref:System.Windows.Interop.HwndSource>定义为视觉对象的父级必须引用你提供的窗口消息筛选器过程的对象。 当您创建<xref:System.Windows.Interop.HwndSource>对象，设置<xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A>属性来引用窗口过程。  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 下面的示例演示用于处理释放鼠标左键和右键消息的代码。 鼠标的坐标值点击位置中的值包含`lParam`参数。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>处理 Win32 消息  
 在下面的示例代码演示如何对主机中包含的视觉对象的层次结构执行命中的测试[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口。 您可以确定一个点是否位于视觉对象的几何内使用<xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>方法，以指定的根可视化对象和针对进行命中测试的坐标值。 在这种情况下，根视觉对象是值<xref:System.Windows.Interop.HwndSource.RootVisual%2A>属性的<xref:System.Windows.Interop.HwndSource>对象。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 有关对视觉对象进行命中测试的详细信息，请参阅[可视化层中的命中测试](hit-testing-in-the-visual-layer.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Interop.HwndSource>
- [使用 Win32 互操作示例命中测试](https://go.microsoft.com/fwlink/?LinkID=159995)
- [可视化层中的命中测试](hit-testing-in-the-visual-layer.md)
