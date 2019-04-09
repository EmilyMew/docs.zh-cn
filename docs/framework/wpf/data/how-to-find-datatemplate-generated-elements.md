---
title: 如何：查找由 DataTemplate 生成的元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: de5a4937feabdb4486d9dcf9d5e5bfddd2356690
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089166"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>如何：查找由 DataTemplate 生成的元素
此示例演示如何查找由 <xref:System.Windows.DataTemplate> 生成的元素。  
  
## <a name="example"></a>示例  
 在此示例中，有一个 <xref:System.Windows.Controls.ListBox> 已绑定到一些 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 数据：  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> 使用以下 <xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 如果想要检索由特定 <xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.DataTemplate> 生成的 <xref:System.Windows.Controls.TextBlock> 元素，需要先获取 <xref:System.Windows.Controls.ListBoxItem>，在该 <xref:System.Windows.Controls.ListBoxItem> 中查找 <xref:System.Windows.Controls.ContentPresenter>，然后在该 <xref:System.Windows.Controls.ContentPresenter> 设置的 <xref:System.Windows.DataTemplate> 上调用 <xref:System.Windows.FrameworkTemplate.FindName%2A> 。 以下示例演示如何执行这些步骤。 出于演示目的，此示例会创建一个消息框，显示 <xref:System.Windows.DataTemplate> 生成的文本块的文本内容。  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 以下是 `FindVisualChild` 的实现，使用了 <xref:System.Windows.Media.VisualTreeHelper> 方法：  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>请参阅

- [如何：查找由 ControlTemplate 生成的元素](../controls/how-to-find-controltemplate-generated-elements.md)
- [数据绑定概述](data-binding-overview.md)
- [帮助主题](data-binding-how-to-topics.md)
- [样式设置和模板化](../controls/styling-and-templating.md)
- [WPF XAML 名称范围](../advanced/wpf-xaml-namescopes.md)
- [WPF 中的树](../advanced/trees-in-wpf.md)
