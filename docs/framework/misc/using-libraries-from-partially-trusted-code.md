---
title: 通过部分受信任的代码使用库
ms.date: 03/30/2017
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a3bbbaa565a6c118082456a1ab6d7af59db7067
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119270"
---
# <a name="using-libraries-from-partially-trusted-code"></a>通过部分受信任的代码使用库
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  本主题介绍强命名程序集的行为，并且仅适用于[级别 1](../../../docs/framework/misc/security-transparent-code-level-1.md)程序集。 [安全透明的代码，级别 2](../../../docs/framework/misc/security-transparent-code-level-2.md)中的程序集[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]或更高版本不受强名称。 有关安全系统更改的详细信息，请参阅[安全更改](../../../docs/framework/security/security-changes.md)。  
  
 不允许未从其主机或沙盒获取完全信任的应用程序调用共享的托管库，除非库编写器明确允许它们使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 特性。 因此，应用程序编写器必须注意某些库在部分受信任的上下文中将不可用。 默认情况下执行的所有代码在部分信任[沙盒](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)和并不处于完全信任程序集的列表为部分受信任。 如果不希望从部分受信任的上下文中执行或由部分受信任的代码调用自己的代码，则不必关心此部分的信息。 但是，如果所编写的代码必须与部分受信任的代码进行交互或从部分受信任的上下文环境进行操作，则应考虑以下因素：  
  
-   为了方便多个应用程序共享库，则必须使用强名称对库进行签名。 强名称允许你的代码可放入全局程序集缓存中或添加到沙盒处理 <xref:System.AppDomain> 的完全信任列表，并允许使用者验证实际来自你的移动代码的特定部分。  
  
-   默认情况下，强名称的[一级](../../../docs/framework/misc/security-transparent-code-level-1.md)共享的库执行隐式[LinkDemand](../../../docs/framework/misc/link-demands.md)信任自动，而无需库编写器无需执行任何操作。  
  
-   如果调用方不具有完全信任但仍尝试调用这样的库，则运行时会引发 <xref:System.Security.SecurityException>，且会不允许调用方链接到库。  
  
-   若要禁用自动**LinkDemand**并避免引发异常，可以将放置**AllowPartiallyTrustedCallersAttribute**上的共享程序集作用域的属性库。 此属性允许从部分受信任的托管代码调用你的库。  
  
-   被授予访问具有此属性的库的权限的部分受信任代码仍将受到由 <xref:System.AppDomain> 定义的进一步限制。  
  
-   部分受信任的代码来调用一个库，它不具有任何通过编程方式**AllowPartiallyTrustedCallersAttribute**属性。  
  
 对特定应用程序都是私有的库不需要强名称或**AllowPartiallyTrustedCallersAttribute**属性，不能引用的应用程序外部的潜在恶意代码。 保护此类代码免受部分受信任的移动代码的有意或无意滥用，而无需开发人员进行任何额外操作。  
  
 你应该考虑显式启用以下代码类型的部分受信任代码的用法：  
  
-   代码已安全漏洞进行认真测试并且符合中所述的准则[安全编码准则](../../../docs/standard/security/secure-coding-guidelines.md)。  
  
-   专门为部分受信任的情况进行编写的强名称代码库。  
  
-   使用强名称签名的任何组件（无论是部分或完全受信任）都将由从 Internet 下载的代码调用。  
  
> [!NOTE]
>  .NET Framework 类库中的某些类不具备**AllowPartiallyTrustedCallersAttribute**属性，不能由部分受信任代码调用。  
  
## <a name="see-also"></a>请参阅

- [代码访问安全性](../../../docs/framework/misc/code-access-security.md)
