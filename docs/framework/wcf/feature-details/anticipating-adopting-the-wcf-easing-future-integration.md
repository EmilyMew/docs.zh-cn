---
title: Windows Communication Foundation 使用展望：轻松实现未来的集成
ms.date: 03/30/2017
ms.assetid: 3028bba8-6355-4ee0-9ecd-c56e614cb474
ms.openlocfilehash: 2f733f9cc33846913539fee4afdd95efa9224058
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124795"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-integration"></a>Windows Communication Foundation 使用展望：轻松实现未来的集成
如果现在使用 ASP.NET，并希望在将来使用 WCF，本主题将提供指南以确保新的 ASP.NET Web 服务，将也与 WCF 应用程序一起正常工作。  
  
## <a name="general-recommendations"></a>一般性建议  
 对任何新服务采用 ASP.NET 2.0。 这样做将允许新服务访问新版本中的改进和增强。 但是，它还将允许在同一应用程序中使用 ASP.NET 2.0 组件以及 WCF 组件的可能性。  
  
## <a name="protocols"></a>协议  
 使用 ASP.NET 2.0 的新工具验证与 WS-I 基本配置文件 1.1 的一致性：  
  
```csharp  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 ASP.NET Web 服务符合 WS-Basic Profile 1.1 将进行互操作与 WCF 客户端使用 WCF 预定义的绑定， <xref:System.ServiceModel.BasicHttpBinding>。  
  
## <a name="service-development"></a>服务开发  
 避免使用 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 特性依据 SOAP 消息正文元素的完全限定名称将消息路由到方法，而应使用 SOAPAction HTTP 标头。 WCF 使用 SOAPAction HTTP 标头来路由消息。  
  
## <a name="data-representation"></a>数据表示形式  
 只要为 XML 显式定义了命名空间，则在默认情况下，<xref:System.Xml.Serialization.XmlSerializer> 将类型序列化为的 XML 与 <xref:System.Runtime.Serialization.DataContractSerializer> 将类型序列化为的 XML 在语义上完全相同。 定义时与 ASP.NET Web 服务一起使用的数据类型并且预期采用 WCF 在将来，执行以下操作：  
  
1.  使用 .NET Framework 类而不是 XML 架构来定义该类型。  
  
2.  仅将 <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.XmlRootAttribute> 添加到该类，使用后者显式定义类型的命名空间。 不要添加 <xref:System.Xml.Serialization> 命名空间中的其他属性来控制如何将 .NET Framework 类转换为 XML。  
  
 通过采用此方法，以后可将 .NET 类转换为附加了 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 的数据协定，而无需为了传输而对类序列化成的 XML 进行重大更改。 将能够作为数据协定由 WCF 应用程序进行处理的消息中使用 ASP.NET Web 服务的类型生成到不同的其他权益，在 WCF 应用程序中更好的性能。  
  
## <a name="security"></a>安全性  
 避免使用 Internet Information Services (IIS) 提供的身份验证选项。 WCF 客户端不支持它们。 如果服务需要提供保护，使用 WCF 提供的因为这些选项更丰富和基于标准协议的选项。  
  
## <a name="see-also"></a>请参阅

- [Windows Communication Foundation 使用展望：轻松实现未来的迁移](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
