---
title: 创建 BindingElement
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 600bf9b394078ffc1b1bc97390bd0de406d64338
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115162"
---
# <a name="creating-a-bindingelement"></a>创建 BindingElement
绑定和绑定元素 (扩展的对象<xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>和<xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>分别) 是 Windows Communication Foundation (WCF) 应用程序模型是与通道工厂和通道侦听器相关联的位置。 无绑定，使用自定义通道需要在通道级编程中所述[服务通道级编程](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)并[客户端通道级编程](../../../../docs/framework/wcf/extending/client-channel-level-programming.md)。 本主题讨论的最低要求若要启用在 WCF，开发中使用您的通道<xref:System.ServiceModel.Channels.BindingElement>通道，和中的步骤 4 中所述的应用程序使用[开发通道](../../../../docs/framework/wcf/extending/developing-channels.md)。  
  
## <a name="overview"></a>概述  
 创建<xref:System.ServiceModel.Channels.BindingElement>为您的通道，开发人员可以在 WCF 应用程序中使用它。 <xref:System.ServiceModel.Channels.BindingElement> 可以通过使用对象<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>类连接到您的通道的 WCF 应用程序，而不必将您的通道的精确类型信息。  
  
 一次<xref:System.ServiceModel.Channels.BindingElement>已被创建，可以启用更多的功能根据您的要求由以下其余通道开发步骤中所述[开发通道](../../../../docs/framework/wcf/extending/developing-channels.md)。  
  
## <a name="adding-a-binding-element"></a>添加绑定元素  
 若要实现自定义 <xref:System.ServiceModel.Channels.BindingElement>，请编写一个继承自 <xref:System.ServiceModel.Channels.BindingElement> 的类。 例如，如果您已开发了一个可以将大消息拆分为多个块并在另一端重新组合这些块的 `ChunkingChannel`，则可以在任意绑定中使用此通道，方法是实现一个 <xref:System.ServiceModel.Channels.BindingElement> 并将绑定配置为使用此元素。 本主题的其余部分以 `ChunkingChannel` 作为示例，演示实现绑定元素的需求。  
  
 `ChunkingBindingElement` 负责创建 `ChunkingChannelFactory` 和 `ChunkingChannelListener`。 它重写 <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> 和 <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> 实现，并检查类型参数是否为 <xref:System.ServiceModel.Channels.IDuplexSessionChannel>（在我们的示例中这是 `ChunkingChannel` 支持的唯一通道形状）以及绑定中的其他绑定元素是否支持此通道形状。  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> 首先检查请求的通道形状可以生成然后获取要分割的消息操作列表。 然后，它创建一个新的 `ChunkingChannelFactory`，并为其传递内部通道工厂。 （如果你要创建传输绑定元素，该元素将是绑定堆栈中的最后一个元素，因此必须创建一个通道侦听器或通道工厂。）  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> 已创建一个类似的实现`ChunkingChannelListener`并将其传递内部通道侦听器。  
  
 使用传输通道，另一个示例[传输：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)示例提供了以下重写。  
  
 在下面的示例中，绑定元素为 `UdpTransportBindingElement`，它派生自 <xref:System.ServiceModel.Channels.TransportBindingElement>。 它重写以下方法以生成与通道关联的工厂。  
  
```csharp  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 它还包含用于克隆 `BindingElement` 并返回我们自己的方案 (soap.udp) 的成员。  
  
#### <a name="protocol-binding-elements"></a>协议绑定元素  
 新绑定元素可以替换或扩充所包括的任何绑定元素，从而添加新的传输、编码或高级协议。 若要创建新的协议绑定元素，请首先扩展 <xref:System.ServiceModel.Channels.BindingElement> 类。 至少，您必须实现<xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType>并实现`ChannelProtectionRequirements`使用<xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>。 这会返回此绑定元素的 <xref:System.ServiceModel.Security.ChannelProtectionRequirements>。  有关详细信息，请参阅 <xref:System.ServiceModel.Security.ChannelProtectionRequirements>。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> 应返回此绑定元素的新副本。 作为一种最佳做法，我们建议绑定元素作者实现 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>，方法是使用复制构造函数首先调用基复制构造函数，然后克隆此类中的所有附加字段。  
  
#### <a name="transport-binding-elements"></a>传输绑定元素  
 若要创建新的传输绑定元素，请扩展 <xref:System.ServiceModel.Channels.TransportBindingElement> 接口。 之后，至少必须实现 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> 方法和 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> 属性。  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> – 应返回此绑定元素的新副本。  作为一种最佳做法，我们建议绑定元素作者实现 Clone，方法是使用可调用基复制构造函数的复制构造函数，然后克隆此类中的任何其他字段。  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> –<xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>获取绑定元素所表示的传输协议的属性返回的 URI 方案。 例如，<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>并<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>从各自返回"http"和"net.tcp"<xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>属性。  
  
#### <a name="encoding-binding-elements"></a>编码绑定元素  
 若要创建新的编码绑定元素，请首先扩展 <xref:System.ServiceModel.Channels.BindingElement> 类并实现 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> 类。 之后，至少必须实现 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> 方法和 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> 属性。  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. 返回此绑定元素的新副本。 作为一种最佳做法，我们建议绑定元素作者实现 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>，方法是使用复制构造函数首先调用基复制构造函数，然后克隆此类中的所有附加字段。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. 返回一个 <xref:System.ServiceModel.Channels.MessageEncoderFactory>，它为实现新编码器的实际类提供句柄并扩展 <xref:System.ServiceModel.Channels.MessageEncoder>。 有关详细信息，请参阅 <xref:System.ServiceModel.Channels.MessageEncoderFactory> 和 <xref:System.ServiceModel.Channels.MessageEncoder>。  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. 返回此编码中使用的 <xref:System.ServiceModel.Channels.MessageVersion>，表示正在使用的 SOAP 和 WS-Addressing 的版本。  
  
 有关用户定义的编码绑定元素的可选方法和属性的完整列表，请参见 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>。  
  
 创建新的绑定元素的详细信息，请参阅[创建用户定义绑定](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。  
  
 为通道创建绑定元素后, 返回到[开发通道](../../../../docs/framework/wcf/extending/developing-channels.md)主题以查看是否想要将配置文件的支持添加到您的绑定元素，如果以及如何添加元数据发布支持和是否以及如何构造用户定义的绑定使用的绑定元素。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.BindingElement>
- [开发通道](../../../../docs/framework/wcf/extending/developing-channels.md)
- [传输：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
