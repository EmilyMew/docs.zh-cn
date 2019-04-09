---
title: 创建 WS-I 基本配置文件 1.1 可互操作服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: b9cacee9a69695b0001b94b74648d5154b8a52b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123911"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a>创建 WS-I 基本配置文件 1.1 可互操作服务
若要配置为可与互操作的 WCF 服务端点[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]Web 服务客户端：  
  
-   将 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> 类型用作服务终结点的绑定类型。  
  
-   不要使用服务终结点上的回调和会话协定功能或事务行为  
  
 你可以根据需要在该绑定上启用对 HTTPS 和传输级客户端身份验证的支持。  
  
 <xref:System.ServiceModel.BasicHttpBinding> 类的以下特性所要求的功能超出了 WS-I 基本配置文件 1.1 的范围：  
  
-   由 <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> 属性控制的消息传递优化机制 (MTOM) 消息编码。 将此属性保留为其默认值（即 <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>）以便不使用 MTOM。  
  
-   由 <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> 值控制的消息安全提供符合 WS-I 基本安全配置文件 1.0 的 WS-Security 支持。 将此属性保留为其默认值（即 <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType>）以便不使用 WS-Security。  
  
 若要使 WCF 服务的元数据可供[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]，使用 Web 服务客户端生成工具：[Web 服务描述语言工具 (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6%28v=vs.100%29)， [Web 服务发现工具 (Disco.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cy2a3ybs%28v=vs.100%29)，和`Add Web Reference`Visual Studio 中的功能; 必须启用元数据发布。 有关详细信息，请参阅[发布元数据终结点](../../../docs/framework/wcf/publishing-metadata-endpoints.md)。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的代码示例演示如何将与兼容的 WCF 终结点添加[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]Web 服务客户端中的代码和配置文件中。  
  
### <a name="code"></a>代码  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a>请参阅

- [与 ASP.NET Web 服务的互操作性](../../../docs/framework/wcf/feature-details/interop-with-aspnet-web-services.md)
