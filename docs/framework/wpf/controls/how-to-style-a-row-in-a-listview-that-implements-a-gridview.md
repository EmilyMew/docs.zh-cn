---
title: 如何：在实现 GridView 的 ListView 中设置行样式
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 9af8d10c7db2d3bbe8b9443402cbb1cfeaa7edb3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091455"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>如何：在实现 GridView 的 ListView 中设置行样式
此示例演示如何在中的行设置样式<xref:System.Windows.Controls.ListView>实现控件<xref:System.Windows.Controls.GridView><xref:System.Windows.Controls.ListView.View%2A>模式。  
  
## <a name="example"></a>示例  
 您可以在中的行设置样式<xref:System.Windows.Controls.ListView>通过设置控件<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>上<xref:System.Windows.Controls.ListView>控件。 表示为其项的样式设置<xref:System.Windows.Controls.ListViewItem>对象。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>引用<xref:System.Windows.Controls.ControlTemplate>用于显示行内容的对象。  
  
 提取了以下示例的完整示例中显示了存储在 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 数据库中的歌曲信息集合。 数据库中的每首歌都有一个评级字段，此字段的值指定了歌曲信息行的显示方式。  
  
 下面的示例演示如何定义<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>为<xref:System.Windows.Controls.ListViewItem>表示歌曲集合中的歌曲的对象。 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>引用<xref:System.Windows.Controls.ControlTemplate>指定如何显示歌曲信息行的对象。  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 下面的示例演示<xref:System.Windows.Controls.ControlTemplate>，它将文本字符串`"Strongly Recommended"`到行。 此模板中引用<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>，并在歌曲的评级的值为 5 （五） 时显示。 <xref:System.Windows.Controls.ControlTemplate>包括<xref:System.Windows.Controls.GridViewRowPresenter>对象，它定义的列中的行的内容布局<xref:System.Windows.Controls.GridView>视图模式。  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 下面的示例定义<xref:System.Windows.Controls.GridView>。  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [帮助主题](listview-how-to-topics.md)
- [ListView 概述](listview-overview.md)
- [样式设置和模板化](styling-and-templating.md)
