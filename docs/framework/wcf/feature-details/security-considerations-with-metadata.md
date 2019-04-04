---
title: 元数据的安全注意事项
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: 2e1ad9f3c7d2a77ec6237bf1fc12c0d1a67181ad
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411908"
---
# <a name="security-considerations-with-metadata"></a>元数据的安全注意事项
时使用的元数据功能的 Windows Communication Foundation (WCF) 中，请考虑发布、 检索和使用服务元数据的安全隐患。  
  
## <a name="when-to-publish-metadata"></a>何时发布元数据  
 默认情况下，WCF 服务不要发布元数据。 若要发布的 WCF 服务的元数据必须显式启用元数据发布到你的服务添加元数据终结点 (请参阅[发布元数据](../../../../docs/framework/wcf/feature-details/publishing-metadata.md))。 禁用元数据发布可以缩小服务的攻击面，同时降低意外泄漏信息的风险。 并非所有服务都必须发布元数据。 如果不必发布元数据，请考虑使其处于关闭状态。 请注意，仍生成直接从您使用的服务程序集的元数据和客户端代码[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 有关使用 Svcutil.exe 导出元数据的详细信息，请参阅[如何：使用 Svcutil.exe 从已编译的服务代码中导出元数据](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)。  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>使用安全绑定发布元数据  
 WCF 提供了不安全的默认元数据绑定和它们允许匿名访问的元数据。 WCF 服务发布服务元数据包含有关服务的详细的说明，可能会有意或无意地包含敏感信息。 例如，服务元数据可能包含有关不希望对外公布的基础结构操作信息。 要防止对服务元数据进行未经授权的访问，您可以对元数据终结点使用安全绑定。 元数据终结点响应可以使用安全套接字层 (SSL) 保护元数据的 HTTP/GET 请求。 有关详细信息，请参阅[如何：保护元数据终结点](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)。  
  
 保护元数据终结点还为请求者提供一种安全检索服务元数据的方法，避免篡改或伪造的风险。  
  
## <a name="using-only-trusted-metadata"></a>仅使用受信任的元数据  
 您可以使用服务元数据自动构造调用服务所需的运行时组件。 还可以在设计时使用元数据来开发客户端应用程序，或在运行时使用元数据动态更新客户端调用服务所使用的绑定。  
  
 当以不安全方式检索服务元数据时，元数据可能会被篡改或伪造。 被篡改的元数据可能会使您的客户端重定向到恶意服务，包含有害的安全设置或包含恶意 XML 结构。 元数据文档可能很大，并且会频繁地保存到文件系统中。 若要防止篡改或伪造，请使用安全绑定来请求服务元数据（如果有安全绑定）。  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>使用安全技术处理元数据  
 使用标准化协议（如 WS-MetadataExchange (MEX)）通过网络从服务频繁检索服务元数据。 许多元数据格式包含引用机制，用以指向其他元数据。 
  <xref:System.ServiceModel.Description.MetadataExchangeClient> 类型会为您自动处理 Web 服务描述语言 (WSDL) 文档、XML 架构和 MEX 文档中的引用。 通过检索到的元数据创建的 <xref:System.ServiceModel.Description.MetadataSet> 对象的大小与使用的 <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> 实例的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 值以及该 `MaxReceivedMessageSize` 实例正在使用的绑定的 <xref:System.ServiceModel.Description.MetadataExchangeClient> 值成正比。 将这些配额设置为您的方案所指示的相应值。  
  
 在 WCF 中，服务元数据作为 XML 进行处理。 当处理 XML 文档时，应用程序应保护自己免受恶意 XML 结构的破坏。 使用<xref:System.Xml.XmlDictionaryReader>与处理 XML 时适当配额，并且还设置<xref:System.Xml.XmlTextReader.DtdProcessing%2A>属性设置为<xref:System.Xml.DtdProcessing.Prohibit>。  
  
 WCF 中的元数据系统是可扩展的可以在应用程序配置文件中注册元数据扩展插件 (请参阅[扩展元数据系统](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md))。 元数据扩展可以运行任意代码，因此，您应利用适合的访问控制列表 (ACL) 来保护应用程序配置文件，并仅注册受信任的元数据扩展实现。  
  
## <a name="validating-generated-clients"></a>验证生成的客户端  
 通过从不受信任的源中检索到的元数据生成客户端代码时，请验证生成的客户端代码，以确保生成的客户端符合你的客户端应用程序安全策略。 您可以使用验证行为来检查客户端绑定上的设置，也可以采用可视化方式来检查工具生成的代码。 有关如何实现验证行为的客户端的示例，请参阅[客户端验证](../../../../docs/framework/wcf/samples/client-validation.md)。  
  
## <a name="protecting-application-configuration-files"></a>保护应用程序配置文件  
 服务的应用程序配置文件可以控制是否发布元数据以及如何发布元数据。 最好利用适当的访问控制列表 (ACL) 来保护应用程序配置文件，以确保攻击者无法修改此类设置。  
  
## <a name="see-also"></a>请参阅
- [如何：保护元数据终结点](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)
- [安全性](../../../../docs/framework/wcf/feature-details/security.md)
