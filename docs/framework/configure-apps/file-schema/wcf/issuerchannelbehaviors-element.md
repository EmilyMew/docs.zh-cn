---
title: <issuerChannelBehaviors> 元素
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7cbd50daa82b0ca937a1bba93786545898b03c8b
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890470"
---
# <a name="issuerchannelbehaviors-element"></a>\<issuerChannelBehaviors > 元素

包含一系列 Windows Communication Foundation (WCF) 客户端终结点行为 （在配置中定义） 以与指定的服务令牌服务通信时使用。 所定义的行为不能包含任何[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)元素。

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a>语法

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a>特性和元素

下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

无。

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|向集合中添加行为。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[\<issuedToken>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|指定用于向服务验证客户端身份的自定义令牌。|

## <a name="remarks"></a>备注

当必须使用任何行为（包含 `<clientCredentials>` 元素的行为除外）与某个服务进行通信时，应使用此元素。 例如，如果[ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)行为元素必须包含。

## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [服务标识和身份验证](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [安全行为](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [联合令牌与颁发的令牌](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [保护服务和客户端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [保证客户端的安全](../../../../../docs/framework/wcf/securing-clients.md)
- [如何：创建联合客户端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [如何：配置本地颁发者](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [联合令牌与颁发的令牌](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
