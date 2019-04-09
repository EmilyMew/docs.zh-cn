---
title: 绑定和绑定元素
ms.date: 03/30/2017
helpviewer_keywords:
- binding elements [WCF]
ms.assetid: 765ff77b-7682-4ea3-90eb-e4d751e37379
ms.openlocfilehash: 33ebb07e350dbbbdd324b442f52dfb6287322bd8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073840"
---
# <a name="bindings-and-binding-elements"></a>绑定和绑定元素
绑定是特殊的配置元素，名为的集合*绑定元素*、 其计算由服务运行时每当客户端或服务终结点构造。 绑定内绑定元素的类型和顺序确定了终结点的通道堆栈中协议和传输通道的选择和堆叠顺序。  
  
 绑定（尤其是系统提供的绑定）通常还具有很多配置属性，这些属性反映了已封装绑定元素的最经常修改的属性。  
  
 绑定必须恰好包含一个传输协议绑定元素。 每个传输协议绑定元素都隐含一个默认的消息编码绑定元素，该元素可以通过向绑定中最多添加一个消息编码绑定元素进行重写。 除了传输协议和编码器绑定元素以外，绑定还可能包含任意数量的协议绑定元素，这些元素共同实现从一个终结点向其他终结点提供和发送 SOAP 消息所需的功能。 有关详细信息，请参阅[到配置服务和客户端使用的绑定](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)。  
  
## <a name="extending-bindings-and-binding-elements"></a>扩展绑定和绑定元素  
 Windows Communication Foundation (WCF) 包含系统提供的绑定，涵盖范围广泛的方案。 (有关详细信息，请参阅[System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)。)可能有时间，但是，当您需要创建和使用不包含在 WCF 中的绑定时。 下面的方案需要创建新绑定。  
  
-   若要使用新的绑定元素（例如，新的传输协议、编码或协议绑定元素），您必须创建一个包含该绑定元素的新绑定。 例如，如果你为 UDP 传输协议添加了一个自定义 `UdpTransportBindingElement`，则需要创建一个新绑定来利用它。 有关执行此行为使用信息<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>类型，请参阅[自定义绑定](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
-   以系统提供的绑定没有在公共属性上公开的方式配置现有绑定元素。 例如，必须创建一个新绑定以更改签名和加密操作的执行顺序。 有关执行此行为的信息，请参阅[如何：自定义系统提供的绑定](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)。  
  
-   建立仅公开特定配置选项的公司标准绑定。 例如，若要为你的公司创建不能禁用安全的 <xref:System.ServiceModel.WSHttpBinding> 变体，可以创建一个行为方式类似于 <xref:System.ServiceModel.WSHttpBinding> 但总是启用安全的新绑定。 有关详细信息，请参阅[创建用户定义绑定](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。  
  
-   若要执行某种元数据自定义，通常可以配置或使用某个自定义绑定元素，但并非必须这样做。 有关向绑定和绑定元素提供元数据支持相关的详细信息，请参阅[配置和元数据支持](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)。  

## <a name="channels-bindings-and-binding-elements"></a>通道、绑定和绑定元素  
 绑定和绑定元素是应用程序编程模型（包括属性和行为）与通道模型（包括工厂和侦听器、消息编码器以及传输协议和协议实现）之间的联系。 通常，实现绑定元素和绑定的目的是使通道能够被应用程序层使用。  
  
 通道层向服务层发送消息或从服务层接收消息，并且在终结点之间传输这些消息。 在客户端上，通道层是一个通道工厂堆栈，这些通道工厂创建通向网络终结点的通道。 在服务上，通道层是一个通道侦听器堆栈，这些侦听器接受在网络终结点收到的通道。  
  
 有两种常规类型的通道：协议通道和传输通道。 传输通道负责在网络终结点之间实际传输消息。 传输通道必须具有默认消息编码器，并且应该能够使用通过消息编码器绑定元素提供的备用消息编码器。 消息编码器负责将 <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> 转换为网络表示以及执行反向转换。 协议通道负责实现 SOAP 级协议（例如，WS-Security 或 WS-ReliableMessaging）。  
  
 传输通道和协议通道的主要要求是它们需要实现必需的通道接口。 若要创建有效的通道层，它们必须具有关联的工厂和侦听器，等等。 若要使用的 WCF 需要有关联的绑定元素中的通道实现派生自<xref:System.ServiceModel.Channels.BindingElement>每个通道和应派生自包括到配置文件的相关的绑定扩展元素<xref:System.ServiceModel.Configuration.BindingElementExtensionElement>.  
  
 如前所述，可以将消息编码器、协议和传输通道实现的绑定元素堆叠起来，以形成一个通道堆栈，而用来将它们组织成一个有序集的机制就是绑定。 绑定和绑定元素将应用程序编程模型与通道模型联系起来。 您可以在代码中直接使用自己的通道实现，但是除非将编码器、传输和协议实现为绑定元素，否则无法在服务层编程模型中使用它们。  
  
 有关开发通道及其绑定元素的详细信息，请参阅[扩展通道层](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。
