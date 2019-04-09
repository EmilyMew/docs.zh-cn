---
title: WF 中的状态机活动
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: 5aee2a7cb078d9d62c9296f7dda9f28ff812a88a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120908"
---
# <a name="state-machine-activities-in-wf"></a>WF 中的状态机活动
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 提供用于创建状态机工作流的多个系统提供的活动和活动设计器。  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|使用熟悉的状态机范例执行包含的活动。|  
|<xref:System.Activities.Statements.State>|代表状态机中的状态。|  
|<xref:System.Activities.Core.Presentation.FinalState>|表示状态机中的终止状态。 <xref:System.Activities.Core.Presentation.FinalState> 为活动设计器，当使用创建<xref:System.Activities.Statements.State>预配置为终止状态。 有关详细信息，请参阅[FinalState 活动设计器](/visualstudio/workflow-designer/finalstate-activity-designer)。|  
|<xref:System.Activities.Statements.Transition>|表示两个状态间的转换。 没有任何**工具箱**项<xref:System.Activities.Statements.Transition>; 通过拖放两个状态之间的一条线方式在工作流设计器上创建转换或通过删除状态时出现的三角形上一个状态悬停在另一个. 有关详细信息，请参阅[Transition 活动设计器](/visualstudio/workflow-designer/transition-activity-designer)。|  
  
## <a name="see-also"></a>请参阅

- [入门教程](getting-started-tutorial.md)
