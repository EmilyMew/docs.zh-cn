---
title: Discovery Find 和 FindCriteria
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: c95f8e1b48c4e58c6d521bd06df4a470999fa375
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095771"
---
# <a name="discovery-find-and-findcriteria"></a>Discovery Find 和 FindCriteria
发现查找操作是发现功能中的主要操作之一，它由客户端启动，用于发现一个或多个服务。 执行查找时将通过网络发送一条 WS-Discovery Probe 消息。 与指定条件匹配的服务通过 WS-Discovery ProbeMatch 消息进行答复。 有关发现消息的详细信息，请参阅[Ws-discovery 规范](https://go.microsoft.com/fwlink/?LinkID=122347)。  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 <xref:System.ServiceModel.Discovery.DiscoveryClient> 类提供执行查找操作的机制，并简化了发现客户端操作的执行过程。 该类包含 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 方法和 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 方法，前者用于执行（阻塞的）同步查找，后者用于启动非阻塞的异步查找。 这两个方法均采用 <xref:System.ServiceModel.Discovery.FindCriteria> 参数，并通过 <xref:System.ServiceModel.Discovery.FindResponse> 对象将结果提供给用户。  
  
## <a name="findcriteria"></a>FindCriteria  
 <xref:System.ServiceModel.Discovery.FindCriteria> 具有多个属性，这可以划分为搜索条件，指定要查找哪些服务，和查找终止条件 （搜索应持续多久）。 <xref:System.ServiceModel.Discovery.FindCriteria> 可包含多个搜索条件。 默认情况下，服务必须与所有组件匹配，否则不会将其自身视为匹配的服务。 如果要查找仅与某些条件匹配的服务，您可以对服务实现自定义查找逻辑，也可以使用多个查询。  
  
 搜索条件包括：  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> -可选。 要搜索的服务的协定名称以及搜索服务时通常采用的条件。 如果指定了多个协定名称，则只有与所有协定均匹配的服务终结点才会进行答复。 请注意，在 WCF 中终结点只能支持一个协定。  
  
-   <xref:System.ServiceModel.Discovery.Configuration.ScopeElement> -可选。 范围表示对各服务终结点进行分类所使用的绝对 URI。 如果多个终结点公开同一协定，并且您希望采用某种方法来搜索终结点的子集，则您可能希望使用此搜索条件。 如果指定了多个范围，则只有与所有范围匹配的服务终结点才会进行答复。  
  
-   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> -指定要匹配的探测消息的终结点的作用域时使用的匹配算法。 支持以下五种范围匹配规则：  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> 区分大小写的基本字符串比较。  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> 由分隔的段的匹配项"/"。 搜索`http://contoso/building1`匹配具有作用域的服务`http://contoso/building/floor1`。 请注意，它不匹配`http://contoso/building100`因为最后两个段不匹配。  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> 按使用 LDAP URL 的段匹配的作用域。  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> 匹配完全使用 UUID 字符串的范围。  
  
    -   <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> 匹配那些未指定范围的服务。  
  
     如果未指定范围匹配规则，则使用 <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix>。  
  
 终止条件包括：  
  
1.  <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 的若要在网络上等待服务所发送答复最长时间。 默认持续时间为 20 秒。  
  
2.  <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 的等待答复最大数目。 如果在经过 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 之前收到了 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 答复，查找操作将结束。  
  
## <a name="findresponse"></a>FindResponse  
 <xref:System.ServiceModel.Discovery.FindResponse> 具有<xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A>集合属性，其中包含匹配服务在网络上的发送的任何相关回复。 如果没有任何服务进行答复，该集合将为空。 如果一个或多个服务进行了答复，则各答复将分别存储在一个 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 对象中，该对象包含有关服务的地址、协定以及某些其他信息。  
  
 下面的示例演示如何在代码中执行查找操作。  
  
```  
// Create DiscoveryClient  
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
// Create FindCriteria  
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));  
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));  
findCriteria.Duration = TimeSpan.FromSeconds(10);   
  
// Find ICalculatorService endpoints              
FindResponse findResponse = discoveryClient.Find(findCriteria);  
  
Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)  
```  
  
## <a name="see-also"></a>请参阅

- [WCF Discovery 概述](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [使用 Discovery 客户端通道](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)
- [通过范围进行发现](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Basic](../../../../docs/framework/wcf/samples/basic-sample.md)
