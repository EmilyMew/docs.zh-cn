---
title: 如何：跨应用程序会话保留和还原应用程序范围属性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application-scope properties [WPF], persisting
- persisting application-scope properties [WPF]
- properties [WPF], persisting
- restoring application-scope properties [WPF]
- properties [WPF], restoring
- application-scope properties [WPF], restoring
ms.assetid: 55d5904a-f444-4eb5-abd3-6bc74dd14226
ms.openlocfilehash: 99b04060d4e7c14313655010dc4fbd5ce1c90487
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134948"
---
# <a name="how-to-persist-and-restore-application-scope-properties-across-application-sessions"></a>如何：跨应用程序会话保留和还原应用程序范围属性
此示例演示如何保留应用程序关闭时，以及如何还原应用程序作用域属性时应用程序下一步是启动应用程序作用域属性。  
  
## <a name="example"></a>示例  
 应用程序仍然存在，应用程序作用域属性，并将其还原从独立存储。 独立的存储是由没有文件访问权限的应用程序可以安全使用的受保护的存储区域。  *App.xaml*文件定义`App_Startup`为处理程序方法<xref:System.Windows.Application.Startup?displayProperty=nameWithType>事件，并且`App_Exit`为处理程序方法<xref:System.Windows.Application.Exit?displayProperty=nameWithType>事件，如突出显示的行的第一个示例中所示。 第二个示例显示了部分*App.xaml.cs*并*App.xaml.vb*突出显示的代码文件`App_Startup`方法，后者将恢复应用程序作用域属性和`App_Exit`方法，将保存应用程序范围的属性。

 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml?highlight=1-7)]
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs?highlight=17-55)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistrestoreappscopepropertiescodebehind1)]
