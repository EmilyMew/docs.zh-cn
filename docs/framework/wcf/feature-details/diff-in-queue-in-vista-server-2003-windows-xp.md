---
title: Windows Vista、Windows Server 2003 和 Windows XP 在排队功能方面的差异
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], differences in operating systems
ms.assetid: aa809d93-d0a3-4ae6-a726-d015cca37c04
ms.openlocfilehash: d13cb3e732d0276902def5de6ca7c007f61b0ec9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115981"
---
# <a name="differences-in-queuing-features-in-windows-vista-windows-server-2003-and-windows-xp"></a>Windows Vista、Windows Server 2003 和 Windows XP 在排队功能方面的差异
本主题总结了在 Windows Communication Foundation (WCF) 队列功能之间的差异[!INCLUDE[wv](../../../../includes/wv-md.md)]， [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]，和[!INCLUDE[wxp](../../../../includes/wxp-md.md)]。  
  
## <a name="application-specific-dead-letter-queue"></a>应用程序特定的死信队列  
 如果接收应用程序未及时读取排队消息，则这些消息可能会无限期保留在队列中。 如果消息的时效性较强则此行为是不适当的。 时效性较强的消息在排队绑定中设置了一个 `TimeToLive` 属性。 此属性指示消息可以在队列中保留多久才会过期。 过期消息将发送到一个称为死信队列的特殊队列中。 消息也可能由于其他原因而在死信队列中终止，如超出队列配额或未通过身份验证。  
  
 通常，共享一个队列管理器的所有排队应用程序存在一个系统范围的死信队列。 使用每个应用程序的死信队列，共享一个队列管理器的各排队应用程序之间可以更好地隔离，方法是允许这些应用程序指定它们自己的应用程序特定的死信队列。 与其他应用程序共享一个死信队列的应用程序必须浏览该队列，以查找对其适用的消息。 对于应用程序特定的死信队列，应用程序可以确保其死信队列中的所有消息都对其适用。  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] 提供有关特定于应用程序的死信队列。 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中未提供应用程序特定的死信队列，因而应用程序必须使用系统范围的死信队列。  
  
## <a name="poison-message-handling"></a>病毒消息处理  
 “病毒消息”是一类已超出向接收应用程序尝试进行传送的最大次数的消息。 当从事务性队列中读取消息的应用程序因出错而无法立即处理消息时，可能会引出现这种情况。 如果应用程序中止从中接收排队消息的事务，则它会将该消息返回到队列。 然后，应用程序尝试在新的事务中再次检索该消息。 如果引起错误的问题未得到纠正，则接收应用程序可能会停留在接收和中止同一条消息的循环中，直到超出最大传送尝试次数并生成病毒消息。  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上的消息队列 (MSMQ) 之间在病毒消息处理方面的主要差异包括以下几点：  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的 MSMQ 支持子队列，而 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 不支持子队列。 子队列用于病毒消息处理。 重试队列和病毒队列是应用程序队列的子队列，是基于病毒消息处理设置创建的。 `MaxRetryCycles` 用于指示要创建的重试子队列的数量。 因此，当在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 或 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上运行时，`MaxRetryCycles` 会被忽略，并且不允许 `ReceiveErrorHandling.Move`。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的 MSMQ 支持否定确认，而 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 不支持。 来自接收队列管理器的否定确认会致使发送队列管理器将被拒绝的消息放入死信队列。 因此，在 `ReceiveErrorHandling.Reject` 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 中不允许 [!INCLUDE[wxp](../../../../includes/wxp-md.md)]。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] 中的 MSMQ 支持用于对消息传递尝试次数进行计数的消息属性。 此中止计数属性在 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 和 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 中不可用。 WCF 会维护中止计数在内存中，所以，此属性可能包含不精确的值时由多个 Web 场中的 WCF 服务读取同一条消息。  
  
## <a name="remote-transactional-read"></a>远程事务性读取  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上的 MSMQ 支持远程事务性读取。 这允许从队列中进行读取的应用程序与该队列承载在不同的计算机上。 这样可以确保服务场能够从中心队列进行读取，从而增加系统的总体吞吐量。 另外，还可以确保在读取和处理消息时一旦出现故障，事务能够回滚并且消息保留在队列中以供以后处理。  
  
## <a name="see-also"></a>请参阅

- [使用死信队列处理消息传输故障](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)
- [病毒消息处理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)
