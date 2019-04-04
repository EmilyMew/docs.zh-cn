---
title: WF 中的事务活动
ms.date: 03/30/2017
ms.assetid: fb33378e-82c6-4ea0-870f-76dc77e7f0fe
ms.openlocfilehash: 7ffd64abdc6edf45174d4b756833d65ec0ef747c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714770"
---
# <a name="transaction-activities-in-wf"></a>WF 中的事务活动
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]包含几个系统提供的活动，它们用于对事务、补偿和取消进行建模。 通过这些编程模型，工作流可以在业务逻辑和错误处理中发生更改时继续向前推进。 有关事务、 补偿和取消的详细信息，请参阅[事务](workflow-transactions.md)，[补偿](compensation.md)，并[取消](modeling-cancellation-behavior-in-workflows.md)。  
  
## <a name="transaction-activities"></a>事务活动  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.CancellationScope>|将活动形式的取消逻辑与执行的主要路径（也表示为活动）相关联。|  
|<xref:System.Activities.Statements.CompensableActivity>|支持对其子活动的补偿。|  
|<xref:System.Activities.Statements.Compensate>|显式调用 <xref:System.Activities.Statements.CompensableActivity> 的补偿处理程序。|  
|<xref:System.Activities.Statements.Confirm>|显式调用 <xref:System.Activities.Statements.CompensableActivity> 的确认处理程序。|  
|<xref:System.Activities.Statements.TransactionScope>|划分事务边界。|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope>|确定接收的消息启动的事务的生存期范围。 事务可以流入发起消息的工作流中，也可以在收到消息时由调度程序创建。 **注意：**<xref:System.ServiceModel.Activities.TransactedReceiveScope>位于**消息传送**一部分**工具箱**。|
