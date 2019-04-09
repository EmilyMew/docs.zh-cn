---
title: <authentication> <serviceCertificate>元素
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: b96d53312d672eebd67de82f69cd9a0a2b5bd22e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117749"
---
# <a name="authentication-of-servicecertificate-element"></a>\<身份验证 > 的\<serviceCertificate > 元素
指定客户端代理用于对使用 SSL/TLS 协商获取的服务证书进行身份验证的设置。  
  
 \<system.ServiceModel>  
\<behaviors>  
endpointBehaviors 部分  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate>  
\<身份验证 >  
  
## <a name="syntax"></a>语法  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|customCertificateValidatorType|字符串。 一个用于验证自定义类型的类型和程序集。|  
|certificateValidationMode|指定用来验证凭据的三种模式之一。 如果设置为 `Custom`，则还必须提供 customCertificateValidator。 默认值为 `ChainTrust`。|  
|revocationMode|用于检查吊销证书列表 (CRL) 的一种模式。 默认值为 `Online`。|  
|trustedStoreLocation|两个系统存储位置之一：`LocalMachine` 或 `CurrentUser`。 在向客户端协商服务证书时使用此值。 对执行验证**受信任的人员**将存储在指定的存储位置。 默认值为 `CurrentUser`。|  
  
## <a name="customcertificatevalidator-attribute"></a>customCertificateValidator 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|String|指定类型名称和程序集以及用于查找类型的其他数据。|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|枚举|以下值之一：None、 PeerTrust、 ChainTrust、 PeerOrChainTrust、 自定义。<br /><br /> 有关详细信息，请参阅[Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## <a name="revocationmode-attribute"></a>revocationMode 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|枚举|以下值之一：NoCheck、 Online 和 Offline。<br /><br /> 有关详细信息，请参阅[Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|枚举|以下值之一：LocalMachine 或 CurrentUser。 默认值为 CurrentUser。 如果客户端应用程序在系统帐户下运行，则证书通常位于 LocalMachine 中。 如果客户端应用程序在用户帐户下运行，则证书通常位于 CurrentUser 中。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|指定客户端对服务进行身份验证时使用的证书。|  
  
## <a name="remarks"></a>备注  
 此配置元素的 `certificateValidationMode` 属性指定用于对证书进行身份验证的信任级别。 默认情况下，该级别设置为 `ChainTrust`，它指定每个证书都必须存在于某个证书层次结构中，而该层次结构以位于证书链顶端的受信任的证书颁发机构结束。 这是最安全的模式。 您还可以将此值设置为 `PeerOrChainTrust`，该值指定受信任的链中的证书以及自行颁发的证书（对等信任）都被接受。 因为不需要从受信任的证书颁发机构那里购买自行颁发的证书，所以可以在开发和调试客户端和服务时使用此值。 在部署客户端时，请改用 `ChainTrust` 值。 您也可以将该值设置为 `Custom` 或 `None`。 若要使用 `Custom` 值，还必须将 `customCertificateValidator` 属性设置为程序集和用于验证证书的类型。 若要创建您自己的自定义验证程序，必须从 X509CertificateValidator 抽象类进行继承。 有关详细信息，请参阅[如何：创建使用自定义证书验证程序的服务](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。  
  
 `revocationMode` 属性指定检查证书是否已吊销的方式。 默认值为 `online`，指示将自动检查证书是否已吊销。 有关详细信息，请参阅[Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
## <a name="example"></a>示例  
 以下示例执行两项任务。 它首先指定客户端使用其域名与终结点进行通信时所使用的服务证书`www.contoso.com`通过 HTTP 协议。 然后，它指定了在身份验证过程中使用的吊销模式和存储位置。  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [安全行为](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [使用证书](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [如何：创建使用自定义证书验证程序的服务](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<身份验证 >](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [保证客户端的安全](../../../../../docs/framework/wcf/securing-clients.md)
- [保护服务和客户端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
