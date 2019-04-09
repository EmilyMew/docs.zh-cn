---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 795e61b9054d2ea9276970988018c50099bcbe17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129644"
---
# <a name="webhttp"></a>\<webHttp>
此元素通过配置指定终结点上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。 此行为与结合使用时[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)标准绑定，使 Windows Communication Foundation (WCF) 服务的 Web 编程模型。  
  
 \<system.ServiceModel>  
\<behaviors>  
\<endpointBehaviors>  
\<behavior>  
\<webHttp>  
  
## <a name="syntax"></a>语法  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|如果此属性设置为 `true`，WCF 基础结构将确定要使用的最佳格式。 默认情况下，禁用自动格式选择，以保证向后兼容性。 可以通过编程方式或配置启用自动格式选择。|  
|defaultBodyStyle|指定返回的消息的默认正文样式。 有关详细信息，请参阅<xref:System.ServiceModel.Web.WebMessageBodyStyle>并[WCF Web HTTP 格式设置](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。|  
|defaultOutgoingResponseFormat|指定消息的默认传出响应格式。 有关详细信息，请参阅[WCF Web HTTP 格式设置](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。|  
|faultExceptionEnabled|获取或设置用于指定在发生内部服务器错误（HTTP 状态代码：500）时是否生成 FaultException 的标志。|  
|helpEnabled|获取或设置一个值，该值确定是否启用了帮助页。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定终结点行为集。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [AJAX 集成和 JSON 支持](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
