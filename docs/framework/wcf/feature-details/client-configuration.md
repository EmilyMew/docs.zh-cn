---
title: 客户端配置
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 1cd7a066622c7d317b1a9c62658531521082c964
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261799"
---
# <a name="client-configuration"></a>客户端配置
Windows Communication Foundation (WCF) 客户端配置可用于指定地址、 绑定、 行为和协定，客户端终结点，哪些客户端用于连接到服务终结点的"ABC"属性。 [\<客户端 >](../../configure-apps/file-schema/wcf/client.md)元素具有[\<终结点 >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)元素，其属性用于配置终结点的 abc 属性。 在讨论这些属性[配置终结点](#configuring-endpoints)部分。  
  
 [\<终结点 >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)元素还包含[\<元数据 >](../../configure-apps/file-schema/wcf/metadata.md)元素用于指定导入和导出元数据，用于设置[ \<标头 >](../../configure-apps/file-schema/wcf/headers.md)包含一个自定义地址标头集合的元素和一个[\<标识 >](../../configure-apps/file-schema/wcf/identity.md)启用的其他终结点的终结点的身份验证的元素交换与它的消息。 [\<标头 >](../../configure-apps/file-schema/wcf/headers.md)并[\<标识 >](../../configure-apps/file-schema/wcf/identity.md)元素属于<xref:System.ServiceModel.EndpointAddress>进行的讨论会在[地址](../../wcf/feature-details/endpoint-addresses.md)一文。 中提供了指向这些主题介绍使用元数据的扩展[配置元数据](#configuring-metadata)部分。  
  
## <a name="configuring-endpoints"></a>配置终结点  
 设计客户端配置为允许客户端可以指定一个或多个终结点，每个都有其自己的名称、 地址和协定，并且每个引用[\<绑定 >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)并[ \<行为 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)要用来配置该终结点的客户端配置中的元素。 客户端配置文件应命名为"App.config"因为这是 WCF 运行时需要的名称。 下面的示例演示一个客户端配置文件。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"   
                 bypassProxyOnLocal="false"   
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"   
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 可选的 `name` 属性唯一地标识了给定协定的终结点。 它由 <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> 或 <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> 用于指定客户端配置中的哪个终结点是目标终结点，必须在创建到服务的通道时加载。 通配符终结点配置名称"\*"可用并且指示<xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A>，就应加载该文件中的任何终结点配置，前提是正好有一个可用，或其他类型的方法将引发异常。 如果省略此属性，则将对应的终结点用作与指定协定类型相关联的默认终结点。 `name` 属性的默认值是一个空字符串，它与任何其他名称一样进行匹配。  
  
 每个终结点都必须具有一个与之关联的地址，用于查找和标识终结点。 `address` 属性可用来指定提供终结点位置的 URL。 但是，通过创建统一资源标识符 (URI)，也可以在代码中指定服务终结点的地址，使用 <xref:System.ServiceModel.ServiceHost> 方法之一可以将该地址添加到 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>。 有关详细信息，请参阅[地址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)。 正如简介， [\<标头 >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)并[\<标识 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)元素属于<xref:System.ServiceModel.EndpointAddress>和中还讨论了[地址](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)主题。  
  
 `binding` 属性指示终结点在连接到服务时期望使用的绑定类型。 该类型必须具有一个已注册的配置节，才能加以引用。 在上一示例中，这是[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)部分中，它指示终结点使用<xref:System.ServiceModel.WSHttpBinding>。 实际上，终结点可以使用某个给定类型的多个绑定。 每个具有其自己[\<绑定 >](../../../../docs/framework/misc/binding.md) (binding) 类型元素中的元素。 `bindingconfiguration` 属性用于区分相同类型的绑定。 其值符合`name`的属性[\<绑定 >](../../../../docs/framework/misc/binding.md)元素。 有关如何配置客户端绑定使用的配置，请参阅[如何：在配置中指定客户端绑定](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)。  
  
 `behaviorConfiguration`属性用于指定哪些[\<行为 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)的[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)终结点应使用。 其值符合`name`的属性[\<行为 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)元素。 有关使用配置来指定客户端行为的示例，请参阅[配置客户端行为](../../../../docs/framework/wcf/configuring-client-behaviors.md)。  
  
 `contract` 属性指定终结点公开哪个协定。 此值对应于 <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> 的 <xref:System.ServiceModel.ServiceContractAttribute>。 默认值为实现相应服务的类的完整类型名。  
  
### <a name="configuring-metadata"></a>配置元数据  
 [\<元数据 >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)元素用于指定导入扩展的设置用于注册元数据。 有关扩展元数据系统的详细信息，请参阅[扩展元数据系统](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)。  
  
## <a name="see-also"></a>请参阅
- [终结点：地址、 绑定和协定](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [配置客户端行为](../../../../docs/framework/wcf/configuring-client-behaviors.md)
