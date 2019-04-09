---
title: 如何：打开消息框
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: cf7534cdee5e17d53e95294573023d660135e395
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101102"
---
# <a name="how-to-open-a-message-box"></a>如何：打开消息框
此示例演示如何以打开一个消息框。  
  
## <a name="example"></a>示例  
 消息框是一种预制模式对话框用于向用户显示的信息。 一个消息框打开通过调用静态<xref:System.Windows.MessageBox.Show%2A>方法的<xref:System.Windows.MessageBox>类。 当<xref:System.Windows.MessageBox.Show%2A>是调用，该消息使用传递的字符串参数。 几个重载<xref:System.Windows.MessageBox.Show%2A>允许你配置如何将出现一个消息框 (请参阅<xref:System.Windows.MessageBox>)。  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>请参阅

- [消息框示例](https://go.microsoft.com/fwlink/?LinkID=160023)
