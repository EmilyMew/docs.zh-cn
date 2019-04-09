---
title: <message> 的 <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 621abbde-590b-454d-90ac-68dc3c69c720
ms.openlocfilehash: 4d9b46b6c148f9280f6504b9bccdf644ab451c00
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102669"
---
# <a name="message-of-wshttpbinding"></a>\<消息 > 的\<wsHttpBinding >
定义的消息级安全性设置[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。  
  
 \<system.ServiceModel>  
\<bindings>  
\<wsHttpBinding>  
\<binding>  
\<安全 >  
\<message>  
  
## <a name="syntax"></a>语法  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
         establishSecurityContext="Boolean"
         negotiateServiceCredential="Boolean" />
```  
  
## <a name="type"></a>类型  
 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|algorithmSuite|设置消息加密和密钥包装算法。 算法和密钥大小由 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> 类确定。 这些算法映射到安全策略语言 (WS-SecurityPolicy) 规范中指定的算法。<br /><br /> 默认值为 `Basic256`。|  
|clientCredentialType|可选。 指定要在使用安全模式执行客户端身份验证时使用的凭据类型是 `Message` 还是 `TransportWithMessageCredentials`。 请参见下面的枚举值。 默认值为 `Windows`。<br /><br /> 此属性的类型为 <xref:System.ServiceModel.MessageCredentialType>。|  
|establishSecurityContext|一个布尔值，确定安全通道是否建立安全会话。 安全会话将在交换应用程序消息之前建立安全上下文令牌 (SCT)。 建立 SCT 时，此安全通道将提供与上层通道之间的 <xref:System.ServiceModel.Channels.ISession> 接口。 有关使用安全会话的详细信息，请参阅[如何：创建安全会话](../../../../../docs/framework/wcf/feature-details/how-to-create-a-secure-session.md)。<br /><br /> 默认值为 `true`。|  
|negotiateServiceCredential|可选。 一个布尔值，指定是在带外客户端提供服务凭据，还是通过协商过程由客户端从服务获取服务凭据。 这种协商是正常消息交换的前提。<br /><br /> 如果`clientCredentialType`属性等于 None、 Username 或 Certificate，此属性设置为`false`意味着服务证书可在带外客户端，并且客户端需要指定服务证书 (使用[ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) 中[ \<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)服务行为。 此模式可与实现 WS-Trust 和 WS-SecureConversation 的 SOAP 堆栈交互操作。<br /><br /> 如果 `ClientCredentialType` 属性设置为 `Windows`，则将此属性设置为 `false` 会指定基于 Kerberos 的身份验证。 这意味着客户端和服务必须是相同 Kerberos 域的一部分。 此模式可与实现 Kerberos 令牌配置文件（如 OASIS WSS TC 中所定义）以及 WS-Trust 和 WS-SecureConversation 的 SOAP 堆栈交互操作。<br /><br /> 当此属性为 `true` 时，会引起通过 SOAP 消息进行 SPNego 交换的 .NET SOAP 协商。<br /><br /> 默认值为 `true`。|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|Basic128|使用 Basic128 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。|  
|Basic192|使用 Basic192 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。|  
|Basic256|使用 Basic256 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。|  
|Basic256Rsa15|对消息加密使用 Basic256，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。|  
|Basic192Rsa15|对消息加密使用 Basic192，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。|  
|TripleDes|使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa-oaep-mgf1p。|  
|Basic128Rsa15|对消息加密使用 Basic128，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。|  
|TripleDesRsa15|使用 TripleDes 加密，对消息摘要使用 Sha1，对密钥包装使用 Rsa15。|  
|Basic128Sha256|对消息加密使用 Basic256，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。|  
|Basic192Sha256|对消息加密使用 Basic192，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。|  
|Basic256Sha256|对消息加密使用 Basic256，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。|  
|TripleDesSha256|对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa-oaep-mgf1p。|  
|Basic128Sha256Rsa15|对消息加密使用 Basic128，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。|  
|Basic192Sha256Rsa15|对消息加密使用 Basic192，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。|  
|Basic256Sha256Rsa15|对消息加密使用 Basic256，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。|  
|TripleDesSha256Rsa15|对消息加密使用 TripleDes，对消息摘要使用 Sha256，对密钥包装使用 Rsa15。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|None|允许服务与匿名客户端交互。 在服务端，这表示该服务不需要任何客户端凭据。 对于客户端，这表示客户端不提供任何客户端凭据。|  
|证书|允许服务要求使用证书对客户端进行身份验证。 如果使用消息安全模式且 `negotiateServiceCredential` 属性设置为 `false`，则需要向客户端提供服务证书。|  
|IssuedToken|指定自定义令牌，该令牌通常由安全令牌服务颁发。|  
|UserName|允许服务要求使用 UserName 凭据对客户端进行身份验证。 WCF 不支持发送密码摘要，也派生密钥使用的密码并使用此类密钥来提供消息安全性。 在这种情况下，WCF 强制使用 UserName 凭据时，传输的安全性。 这种凭据模式将产生可互操作的交换或不可互操作的协商，具体取决于 `negotiateServiceCredential` 属性。|  
|Windows|允许 SOAP 交换在已通过身份验证的 Windows 凭据上下文中执行。 如果 `negotiateServiceCredential` 属性设置为 `true`，则将执行 SSPI 协商或 Kerberos（一种可互操作的标准）。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<安全 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|定义的安全设置[ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.NonDualMessageSecurityOverHttpElement>
- [保护服务和客户端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [绑定](../../../../../docs/framework/wcf/bindings.md)
- [配置系统提供的绑定](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用绑定配置服务和客户端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
