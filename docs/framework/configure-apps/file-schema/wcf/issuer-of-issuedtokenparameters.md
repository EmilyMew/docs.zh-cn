---
title: <issuer> 的 <issuedTokenParameters>
ms.date: 03/30/2017
ms.assetid: d6a95f32-d58c-40fc-8658-dd92564d3c90
ms.openlocfilehash: 690ab14ea33ba9bef29788b2eb35f86ed945ce2b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113537"
---
# <a name="issuer-of-issuedtokenparameters"></a>\<issuer> of \<issuedTokenParameters>
指定颁发安全令牌的安全令牌服务 (STS)。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<安全 >  
\<issuedTokenParameters>  
\<issuer>  
  
## <a name="syntax"></a>语法  
  
```xml  
<issuer address="Uri" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|地址|必选字符串。 STS 的 URL。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|生成器可以创建的终结点的地址标头的集合。|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|在使用颁发的令牌时，指定能够使客户端对服务器进行身份验证的设置。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<issuedTokenParameters>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|指定当前颁发的令牌。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.AdditionalRequestParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [服务标识和身份验证](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [联合令牌与颁发的令牌](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [使用自定义绑定的安全功能](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [联合令牌与颁发的令牌](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [绑定](../../../../../docs/framework/wcf/bindings.md)
- [扩展绑定](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自定义绑定](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [如何：使用 SecurityBindingElement 创建自定义绑定](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [自定义绑定安全性](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
