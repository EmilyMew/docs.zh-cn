---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 266b33e9b0386d0346a86ba8bd82cc65def4f0c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180149"
---
# <a name="endtoendtracing"></a>\<endToEndTracing>
一个配置元素，用于启用和禁用服务应用程序运行过程中端对端跟踪的不同方面。  
  
 \<system.ServiceModel>  
\<diagnostic>  
\<endToEndTracing>  
  
## <a name="syntax"></a>语法  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`activityTracing`|一个布尔值，指定是否启用活动跟踪。|  
|`messageFlowTracing`|一个布尔值，指定是否启用消息流跟踪。|  
|`propagateActivity`|一个布尔值，指定是否将传播特性设置为 true。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<diagnostics>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|定义管理员运行时检查和控制的 WCF 设置。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [端到端跟踪](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
