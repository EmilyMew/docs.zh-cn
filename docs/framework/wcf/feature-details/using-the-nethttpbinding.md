---
title: 使用 NetHttpBinding
ms.date: 03/30/2017
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
ms.openlocfilehash: 5090cfdfeb068acda1e1092e408f3cd747c574c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121012"
---
# <a name="using-the-nethttpbinding"></a>使用 NetHttpBinding
<xref:System.ServiceModel.NetHttpBinding> 是为使用 HTTP 或 WebSocket 服务而设计的绑定，并使用默认情况下的二进制编码。 <xref:System.ServiceModel.NetHttpBinding> 将检测它是否与请求-答复协定或双工协定一起使用，并更改其行为以进行匹配-它将使用 HTTP 的请求-答复协定和 Websocket 的双工协定。 可使用 <xref:System.ServiceModel.Channels.WebSocketTransportUsage> 设置来重写此行为：  
  
1. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Always> -这会强制甚至对于请求-答复协定使用 Websocket。  
  
2. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.Never> -这可以防止使用 Websocket。 尝试使用具有此设置的双工协定将导致异常。  
  
3. <xref:System.ServiceModel.Channels.WebSocketTransportUsage.WhenDuplex> -这是默认值，如上文所述的行为。  
  
 <xref:System.ServiceModel.NetHttpBinding> 在 HTTP 模式和 WebSocket 模式下支持可靠会话。 在 WebSocket 模式下，会话由传输来提供。  
  
> [!WARNING]
>  在使用 <xref:System.ServiceModel.NetHttpBinding> 且该绑定的 TransferMode 设置为 TransferMode.Streamed 时，较大的流可能会造成死锁，调用将会超时。 若要解决此问题，请发送较小的流，或使用 TransferMode.Buffered。  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a>将服务配置为使用 NetHttpBinding  
 <xref:System.ServiceModel.NetHttpBinding> 的配置方式与任何其他绑定的配置方式相同。 以下配置代码段说明了如何通过 <xref:System.ServiceModel.NetHttpBinding> 配置 WCF 服务。  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    ...
  </system.serviceModel>  
```  
  
 下面的代码段演示如何用代码添加 <xref:System.ServiceModel.NetHttpBinding>。  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a>请参阅

- [配置服务绑定](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)
- [绑定](../../../../docs/framework/wcf/feature-details/bindings.md)
- [系统提供的绑定](../../../../docs/framework/wcf/system-provided-bindings.md)
- [双工服务](../../../../docs/framework/wcf/feature-details/duplex-services.md)
