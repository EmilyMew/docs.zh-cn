---
title: 如何：在事件处理程序中查找源元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: 9a49878c9ad8313903df4506796998fd43e2e749
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104554"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>如何：在事件处理程序中查找源元素
此示例演示如何在事件处理程序中查找源元素。  
  
## <a name="example"></a>示例  
 下面的示例演示<xref:System.Windows.Controls.Primitives.ButtonBase.Click>在代码隐藏文件中声明的事件处理程序。 当用户单击处理程序附加到的按钮时，该处理程序更改的属性值。 处理程序代码使用<xref:System.Windows.RoutedEventArgs.Source%2A>路由的事件数据中的事件自变量报告更改的属性<xref:System.Windows.FrameworkElement.Width%2A>上的属性值<xref:System.Windows.RoutedEventArgs.Source%2A>元素。  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.RoutedEventArgs>
- [路由事件概述](routed-events-overview.md)
- [帮助主题](events-how-to-topics.md)
