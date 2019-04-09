---
title: 如何：使用代码添加事件处理程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: 10f8e0899e61d5d54589c910bdcbcd92d8ee947c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129351"
---
# <a name="how-to-add-an-event-handler-using-code"></a>如何：使用代码添加事件处理程序
此示例演示如何使用代码将事件处理程序添加到元素。  
  
 如果你想要添加到事件处理程序[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]已加载元素，并包含的元素的标记页面，则必须添加使用代码处理程序。 或者，如果您正在生成的应用程序完全使用代码而没有声明使用任何元素的元素树[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]，可以调用特定方法来将事件处理程序添加到构造的元素树。  
  
## <a name="example"></a>示例  
 下面的示例添加一个新<xref:System.Windows.Controls.Button>到现有的页面中最初定义[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 代码隐藏文件实现事件处理程序方法，然后将该方法添加为新的事件处理程序上<xref:System.Windows.Controls.Button>。  
  
 C#的示例使用`+=`运算符分配的事件处理程序。 这是用于分配中的处理程序的相同运算符[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]事件处理模型。 作为一种方式添加事件处理程序的情况下，Microsoft Visual Basic 不支持此运算符。 相反，它要求两种技术之一：  
  
-   使用<xref:System.Windows.UIElement.AddHandler%2A>方法，一起`AddressOf`运算符，以引用的事件处理程序实现。  
  
-   使用`Handles`关键字作为事件处理程序定义的一部分。 此处; 未显示这种方法请参阅[Visual Basic 和 WPF 事件处理](visual-basic-and-wpf-event-handling.md)。  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  添加事件处理程序在最初分析[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]页是要简单得多。 在对象元素中你想要添加事件处理程序，将添加匹配你想要处理的事件名称的属性。 然后该属性的值指定的代码隐藏文件中定义的事件处理程序方法的名称为[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]页。 有关详细信息，请参阅[XAML 概述 (WPF)](xaml-overview-wpf.md)或[路由事件概述](routed-events-overview.md)。  
  
## <a name="see-also"></a>请参阅

- [路由事件概述](routed-events-overview.md)
- [帮助主题](events-how-to-topics.md)
