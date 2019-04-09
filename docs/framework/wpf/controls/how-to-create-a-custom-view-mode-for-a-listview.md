---
title: 如何：创建 ListView 的自定义视图模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], creating custom View mode
ms.assetid: 71077349-eeb9-4344-ab29-b5df96df3314
ms.openlocfilehash: de11250a2e7529fba3b262e42b6714262738fa90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092885"
---
# <a name="how-to-create-a-custom-view-mode-for-a-listview"></a>如何：创建 ListView 的自定义视图模式
此示例演示如何创建自定义<xref:System.Windows.Controls.ListView.View%2A>模式<xref:System.Windows.Controls.ListView>控件。  
  
## <a name="example"></a>示例  
 必须使用<xref:System.Windows.Controls.ViewBase>类创建的自定义视图时<xref:System.Windows.Controls.ListView>控件。 下面的示例演示调用的视图模式`PlainView`，它派生自<xref:System.Windows.Controls.ViewBase>类。  
  
 [!code-csharp[ListViewCustomView#PlainView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/PlainView.cs#plainview)]
 [!code-vb[ListViewCustomView#PlainView](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/plainview.vb#plainview)]  
  
 若要将样式应用到自定义视图，请使用<xref:System.Windows.Style>类。 下面的示例定义<xref:System.Windows.Style>为`PlainView`视图模式。 在上一示例中，此样式设置的值作为<xref:System.Windows.Controls.ViewBase.DefaultStyleKey%2A>属性，可为定义`PlainView`。  
  
 [!code-xaml[ListViewCustomView#PlainViewStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Themes/Generic.xaml#plainviewstyle)]  
  
 若要在自定义视图模式中定义的数据布局，定义<xref:System.Windows.DataTemplate>对象。 下面的示例定义<xref:System.Windows.DataTemplate>可用来显示数据中的`PlainView`视图模式。  
  
 [!code-xaml[ListViewCustomView#PlainViewDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewdatatemplate)]  
  
 下面的示例演示如何定义<xref:System.Windows.ResourceKey>有关`PlainView`使用的视图模式<xref:System.Windows.DataTemplate>上一示例中定义。  
  
 [!code-xaml[ListViewCustomView#PlainViewtileView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml#plainviewtileview)]  
  
 一个<xref:System.Windows.Controls.ListView>控件可以使用自定义视图，如果您设置<xref:System.Windows.Controls.ListView.View%2A>属性设置为资源键。 下面的示例演示如何指定`PlainView`的视图模式<xref:System.Windows.Controls.ListView>。  
  
 [!code-csharp[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp/Window1.xaml.cs#listviewtileviewmode)]
 [!code-vb[ListViewCustomView#ListViewtileViewmode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic/window1.xaml.vb#listviewtileviewmode)]  
  
 有关完整示例，请参阅[具有多个视图的 ListView (C#)](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/ListViewCustomView/CSharp)或[ListView 与多个 Views(Visual Basic)](https://github.com/dotnet/samples/tree/master/snippets/visualbasic/VS_Snippets_Wpf/ListViewCustomView/visualbasic)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [帮助主题](listview-how-to-topics.md)
- [ListView 概述](listview-overview.md)
- [GridView 概述](gridview-overview.md)
