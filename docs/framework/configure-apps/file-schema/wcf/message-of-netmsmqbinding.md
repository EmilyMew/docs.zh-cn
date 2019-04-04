---
title: <message> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: c623b7daf1e91c9c1800b9653525cd51b1087506
ms.sourcegitcommit: 5c2176883dc3107445702724a7caa7ac2f6cb0d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/03/2019
ms.locfileid: "58890561"
---
# <a name="message-of-netmsmqbinding"></a>\<message> of \<netMsmqBinding>

在此 `netMsmqBinding` 绑定上定义 SOAP 消息安全设置。

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

## <a name="syntax"></a>语法

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a>特性和元素

下列各节描述了特性、子元素和父元素。

### <a name="attributes"></a>特性

|特性|描述|
|---------------|-----------------|
|algorithmSuite|设置消息加密和密钥包装算法，这些算法用于针对通过 MSMQ 传输发送的消息实现基于消息的安全性。<br /><br /> 默认值为 `Aes256`。 此属性的类型为 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>。|
|clientCredentialType|指定针对通过 MSMQ 传输发送的消息执行客户端身份验证时要使用的凭据类型。 包括以下有效值：<br /><br /> -None:允许服务与匿名客户端交互。 服务和客户端都不需要凭据。<br />-Windows:这使经过身份验证的 Windows 凭据上下文中进行 SOAP 交换。 此设置总是执行基于 Kerberos 的身份验证。<br />-UserName:这使服务可以要求客户端进行身份验证使用用户名凭据。 在这种情况下需要使用指定凭据`clientCredentials`行为**警告：** Windows Communication Foundation (WCF) 不支持发送密码摘要，也派生密钥使用的密码并使用此类密钥来提供消息安全性。 因此，WCF 强制使用 UserName 凭据时，交换的安全性。 此模式要求使用 `clientCredential` 行为和 `serviceCertificate` 在客户端指定服务证书。 <br /><br /> -证书：这使服务可以要求客户端进行身份验证使用的证书。 在此情况下，需要使用 `clientCredentials` 行为指定客户端凭据。 在此情况下，需要使用 `clientCredentials` 行为，通过指定 `serviceCertificate` 来指定服务凭据。<br />-CardSpace:这允许服务要求客户端进行身份验证使用 CardSpace。 必须在 `serviceCertificate` 行为中设置 `clientCredential`。<br /><br /> 默认值为 `Windows`。 此属性的类型为 <xref:System.ServiceModel.MessageCredentialType>。|

### <a name="child-elements"></a>子元素

None

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|[\<安全 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|定义绑定的安全设置。|

## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [WCF 中的队列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [保护服务和客户端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [绑定](../../../../../docs/framework/wcf/bindings.md)
- [配置系统提供的绑定](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用绑定配置服务和客户端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
