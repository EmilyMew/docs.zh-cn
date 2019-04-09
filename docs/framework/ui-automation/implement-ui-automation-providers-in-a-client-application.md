---
title: 在客户端应用程序中实现 UI 自动化提供程序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: b368ab3bc842fda5a99a64e0220093ebd60698b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105919"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>在客户端应用程序中实现 UI 自动化提供程序
> [!NOTE]
>  本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，请参阅[Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主题所包含的代码示例演示如何在应用程序中实现客户端 UI 自动化提供程序。  
  
 这种情况不常见。 通常，UI 自动化客户端应用程序使用服务器端提供程序或驻留在 DLL 中的客户端提供程序。  
  
## <a name="example"></a>示例  
 下面的代码示例实现了一个简单的控制台窗口提供程序。 此代码没有任何有用的功能，只是用于演示在客户端代码中设置提供程序以及使用 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>注册此提供程序的基本步骤。  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>请参阅

- [UI 自动化提供程序概述](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [注册客户端提供程序程序集](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [创建客户端 UI 自动化提供程序](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [客户端 UI 自动化提供程序的实现](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
