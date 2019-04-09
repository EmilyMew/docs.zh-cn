---
title: 如何：使用 Win32 宿主容器进行命中测试
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], using Win32 host containers
- visual objects [WPF], hit tests on
- Win32 host containers [WPF], hit tests using
ms.assetid: 9491f7f3-d8ba-4573-a888-2f064d1349dc
ms.openlocfilehash: ac5cae5bcd94dc8bf80ff95b8971914e1fa5ba2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081458"
---
# <a name="how-to-hit-test-using-a-win32-host-container"></a>如何：使用 Win32 宿主容器进行命中测试
可以创建视觉对象中的[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]通过视觉对象提供宿主窗口容器的窗口。 若要为包含的视觉对象提供事件处理，需要处理传递到宿主窗口容器的消息筛选器循环的消息。 请参阅[教程：承载在 Win32 应用程序中的视觉对象](tutorial-hosting-visual-objects-in-a-win32-application.md)有关详细信息如何托管中的可视化对象[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]窗口。  
  
## <a name="example"></a>示例  
 下面的代码演示如何设置鼠标事件处理程序为[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]用作视觉对象的宿主容器的窗口。  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
 下面的示例演示如何设置命中测试来响应捕获特定的鼠标事件。  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 <xref:System.Windows.Interop.HwndSource>对象表示[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]中的内容[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]窗口。 值<xref:System.Windows.Interop.HwndSource.RootVisual%2A>属性的<xref:System.Windows.Interop.HwndSource>对象都表示可视化树层次结构中的最顶层节点。  
  
 有关使用 Win32 宿主容器对象时进行命中测试的完整示例，请参阅[使用 Win32 互操作示例命中测试](https://go.microsoft.com/fwlink/?LinkID=159995)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Interop.HwndSource>
- [可视化层中的命中测试](hit-testing-in-the-visual-layer.md)
- [教程：在 Win32 应用程序中承载视觉对象](tutorial-hosting-visual-objects-in-a-win32-application.md)
