---
title: 实例数
ms.date: 03/30/2017
ms.assetid: c8cf3460-0ca1-4411-8262-e9ecaf7f0a31
ms.openlocfilehash: 668cfb3026b9ab7259665f5e53873a512b1e2238
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118984"
---
# <a name="instances"></a>实例数
计数器名称：实例。  
  
## <a name="description"></a>描述  
 服务当前包含的实例上下文的数量。  
  
 在大部分时间里，实例上下文的数量都等于实例数。 但是，下列方案例外。  
  
-   服务方法显式调用 <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> 方法。  
  
-   一个 <xref:System.ServiceModel.ReleaseInstanceMode> 被应用于一个 <xref:System.ServiceModel.OperationBehaviorAttribute> 实例。  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.OperationBehaviorAttribute>
