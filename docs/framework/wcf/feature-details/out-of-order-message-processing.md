---
title: 无序消息处理
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4e1864b25a4dbe8192cd5c692c75645bebbb92d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141396"
---
# <a name="out-of-order-message-processing"></a>无序消息处理
工作流服务可能依赖于按特定顺序发送的消息。 工作流服务包含一个或多个 <xref:System.ServiceModel.Activities.Receive> 活动，而每个 <xref:System.ServiceModel.Activities.Receive> 活动需要一条特定消息。 如果无法保证单独传递传输，客户端发送的消息可能会延迟，从而可能无法按工作流服务所需的顺序传递消息。 实现无需按特定顺序传送消息的工作流服务时，通常使用并行活动来完成此操作。 对于更复杂的应用程序协议，工作流将很快变得极其复杂。  无序消息处理功能在 Windows Communication Foundation (WCF)，可创建此类工作流所有嵌套并行活动的复杂性。 支持的通道仅支持无序消息处理<xref:System.ServiceModel.Channels.ReceiveContext>如 WCF MSMQ 绑定。  
  
## <a name="enabling-out-of-order-message-processing"></a>启用无序消息处理  
 在 WorkflowService 上将 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 属性设置为`true` 即会启用无序消息处理。 下面的示例演示如何在代码中设置 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 属性。  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 还可以将 `AllowBufferedReceive` 特性应用到 XAML 中的工作流服务，如下面的示例所示。  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [工作流服务](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [队列和可靠会话](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
