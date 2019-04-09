---
title: 如何：使用 IScrollInfo 接口滚动内容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ScrollViewer control [WPF], scrolling content
- scrolling content [WPF]
- IScrollInfo interface [WPF]
ms.assetid: d8700bef-a3f8-4c12-9de2-fc3b79f32cd3
ms.openlocfilehash: 6ebd8268e1358b45709885c07e6b096d5f806ebb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098541"
---
# <a name="how-to-scroll-content-by-using-the-iscrollinfo-interface"></a>如何：使用 IScrollInfo 接口滚动内容
此示例演示如何通过使用滚动内容<xref:System.Windows.Controls.Primitives.IScrollInfo>接口。  
  
## <a name="example"></a>示例  
 下面的示例演示的功能<xref:System.Windows.Controls.Primitives.IScrollInfo>接口。 此示例将创建<xref:System.Windows.Controls.StackPanel>中的元素[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]嵌套在父<xref:System.Windows.Controls.ScrollViewer>。 子元素<xref:System.Windows.Controls.StackPanel>可以通过使用定义的方法以逻辑方式滚动<xref:System.Windows.Controls.Primitives.IScrollInfo>界面和强制转换为的实例<xref:System.Windows.Controls.StackPanel>(`sp1`) 在代码中。  
  
 [!code-xaml[IScrollInfoMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml#2)]  
  
 每个<xref:System.Windows.Controls.Button>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]文件触发控制滚动行为中的关联自定义方法<xref:System.Windows.Controls.StackPanel>。 下面的示例演示如何使用<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A>并<xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>方法; 它还以一般方式演示如何使用所有定位方法的<xref:System.Windows.Controls.Primitives.IScrollInfo>类定义。  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- <xref:System.Windows.Controls.StackPanel>
- [ScrollViewer 概述](scrollviewer-overview.md)
- [帮助主题](scrollviewer-how-to-topics.md)
- [面板概述](panels-overview.md)
