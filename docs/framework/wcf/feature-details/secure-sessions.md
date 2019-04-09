---
title: 安全会话
ms.date: 03/30/2017
ms.assetid: 7b50602f-d7b5-42e9-8e92-1f0413df0d8b
ms.openlocfilehash: 8f5cf9a965951bcc1049c2e96ae6cfa80b0113ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084945"
---
# <a name="secure-sessions"></a>安全会话
Windows Communication Foundation (WCF) 的一项功能是保证按发送的顺序接收消息的可靠会话。 本节中的主题讨论在创建可靠会话时要考虑的安全性问题。 有关可靠会话的详细信息，请参阅[使用会话的](../../../../docs/framework/wcf/using-sessions.md)。  
  
> [!NOTE]
>  当需要在 Windows XP 上进行模拟时，请不要在安全会话中使用有状态安全令牌上下文 (SCT)。 如果在模拟时使用有状态 SCT，则会引发 <xref:System.InvalidOperationException>。 有关详细信息，请参阅[不支持的方案](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)。  
  
## <a name="in-this-section"></a>本节内容  
  
|||  
|-|-|  
|[安全对话和安全会话](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)|安全对话和安全会话是同义词。 本主题解释安全对话的工作方式以及使用该模式的时机和原因。|  
|[如何：创建安全会话](../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)|演练创建安全会话的基本操作。|  
|[如何：为安全会话创建安全上下文令牌](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)|演练创建能够保持状态以及与客户端之间会话的网络场的步骤。|  
|[安全会话的安全注意事项](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md)|描述安全会话的特殊注意事项。|  
  
## <a name="reference"></a>参考  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a>相关章节  
 [会话、实例化和并发](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
  
 [设计和实现服务](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="see-also"></a>请参阅

- [如何：启用消息重放检测](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)
- [重播攻击](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [如何：创建要求会话的服务](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
