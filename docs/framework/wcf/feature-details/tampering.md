---
title: 篡改
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 7a4265c30a6713f9557de2b3d1e99c87b7dd3e58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107882"
---
# <a name="tampering"></a>篡改
*篡改*是一条消息或传送的消息时，更改，并且为它的本来目的使用更改后的消息的行为。  
  
## <a name="do-not-disable-ws-addressing"></a>不要禁用 WS-Addressing  
 WS-Addressing 规范在每条消息中提供了地址标头，从而允许消息接收方验证消息的发送方。 将 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 属性设置为 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> 可禁用此功能。  
  
 当安全模式设置为“消息”并且禁用了 WS-Addressing 时，攻击者就能获取来自客户端的请求，并将其发送到另一个服务，而第二个服务无法检测该消息是否来自于原客户端。 实际上，第一个服务在与第二个服务通信时，可假装它是一个客户端。  
  
 为了避免这个问题，请不要将 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 属性设置为 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，并避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，如静态 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 属性，它会将 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 属性设置为 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。  
  
## <a name="see-also"></a>请参阅

- [安全注意事项](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [信息泄露](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [特权提升](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [拒绝服务](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [不支持的方案](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [重播攻击](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
