---
title: <transport> 的 <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ec726c4b39fedbf63a7ecc9e685a86367609fa43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084998"
---
# <a name="transport-of-netmsmqbinding"></a>\<传输 > 的\<netMsmqBinding >
定义传输安全设置。  
  
 \<system.ServiceModel>  
\<bindings>  
\<netMsmqBinding>  
\<binding>  
\<安全 >  
\<transport>  
  
## <a name="syntax"></a>语法  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|msmqAuthenticationMode|指定 MSMQ 传输必须采用什么方式对消息进行身份验证。 包括以下有效值：<br /><br /> -None:无身份验证。<br />-   WindowsDomain:身份验证机制使用 Active Directory 检索与消息关联的安全标识符的 X.509 证书。 然后使用它来检查队列的 ACL 以确保用户具有队列写权限。<br />-证书：通道从证书存储检索证书。<br /><br /> 默认值为 `WindowsDomain`。<br /><br /> 如果将此属性设置为 `None`，则 `msmqProtectionLevel` 属性也必须设置为 `None`。 此属性是类型的 <xref:System.ServiceModel.MsmqAuthenticationMode>|  
|msmqEncryptionAlgorithm|指定在消息队列管理器之间传输消息时用于在网络上对消息进行加密的算法。 包括以下有效值：<br /><br /> -   RC4Stream<br />-   AES<br />-默认值是`RC4Stream`。 此属性的类型为 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。|  
|msmqProtectionLevel|指定在 MSMQ 传输级别采用什么方式来保护消息。 加密可确保消息的完整性，而签名和加密不仅可以确保消息的完整性，还可以确保消息的不可否认性。 也就是说，消息确实来自发送者，发送者与他所声称的身份一致。 包括以下有效值：<br /><br /> -None:无保护。<br />登录：对消息进行签名。<br />-EncryptAndSign:对消息进行加密和签名。<br />-默认值是`Sign`。|  
|msmqSecureHashAlgorithm|指定用于计算消息摘要的哈希算法。 包括以下有效值：<br /><br /> -   MD5<br />-   SHA1<br />-   SHA256<br />-   SHA512<br /><br /> 默认值为 `SHA1`。 此属性的类型为 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。<br>由于存在冲突问题 MD5 和 SHA1，Microsoft 建议 SHA256 或更好的。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<安全 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|定义排队传输的传输安全设置。|  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [WCF 中的队列](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [保护服务和客户端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [绑定](../../../../../docs/framework/wcf/bindings.md)
- [配置系统提供的绑定](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用绑定配置服务和客户端](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
