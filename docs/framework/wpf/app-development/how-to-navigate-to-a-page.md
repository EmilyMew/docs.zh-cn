---
title: 如何：转到页面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: c8e808180682bfd97f397d8cadd1e4deafd7eb06
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141045"
---
# <a name="how-to-navigate-to-a-page"></a>如何：转到页面
此示例演示了几种方法在其中一个页面可以导航到从<xref:System.Windows.Navigation.NavigationWindow>。  
  
## <a name="example"></a>示例  
 很可能<xref:System.Windows.Navigation.NavigationWindow>以导航到页面使用以下值之一：  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A> 属性。  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> 方法。  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] 可以是相对值还是绝对值。 有关详细信息，请参阅 [WPF 中的 Pack URI](pack-uris-in-wpf.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
