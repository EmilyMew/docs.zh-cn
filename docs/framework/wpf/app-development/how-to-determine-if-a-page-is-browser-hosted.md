---
title: 如何：确定是否是浏览器托管页面
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosted pages in browser [WPF]
- pages [WPF], hosted in browser
ms.assetid: 737e0f26-8371-49b4-9579-70879e51e1aa
ms.openlocfilehash: d154de2f885101d1bd0c4613dfb1604be8acbe6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107141"
---
# <a name="how-to-determine-if-a-page-is-browser-hosted"></a>如何：确定是否是浏览器托管页面
此示例演示如何确定如果<xref:System.Windows.Controls.Page>托管浏览器中。  
  
## <a name="example"></a>示例  
 一个<xref:System.Windows.Controls.Page>可以是主机不可知的因此，可以将加载到多个不同类型的主机，包括<xref:System.Windows.Controls.Frame>、 <xref:System.Windows.Navigation.NavigationWindow>，或浏览器。 发生此情况有一个库程序集，其中包含一个或多个页面，以及哪一个是引用由多个独立的和可浏览 ([!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]) 托管应用程序。  
  
 下面的示例演示如何使用<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>来确定如果<xref:System.Windows.Controls.Page>托管浏览器中。  
  
 [!code-csharp[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/CSharp/Page1.xaml.cs#isbrowserhostedcode)]
 [!code-vb[HOWTOBrowserInteropHelperSnippets#IsBrowserHostedCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOBrowserInteropHelperSnippets/visualbasic/page1.xaml.vb#isbrowserhostedcode)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
