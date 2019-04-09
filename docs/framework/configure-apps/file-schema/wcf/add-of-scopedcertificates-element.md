---
title: <add> <scopedCertificates>元素
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: 06a624d0146745581dfe907d044d1f7d3b857902
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119673"
---
# <a name="add-of-scopedcertificates-element"></a>\<添加 > 的\<scopedCertificates > 元素
向作用域证书集合添加 X.509 证书。  
  
 \<system.ServiceModel>  
\<behaviors>  
endpointBehaviors 部分  
\<behavior>  
\<clientCredentials>  
\<serviceCertificate>  
\<scopedCertificates>  
\<add> element for \<scopedCertificates>  
  
## <a name="syntax"></a>语法  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|targetUri|字符串。 指定与证书相关的服务的 URI。|  
|findValue|字符串。 要搜索的值。|  
|x509FindType|枚举。 要搜索的证书字段之一。|  
|storeLocation|枚举。 要搜索的两个存储位置之一。|  
|storeName|枚举。 要搜索的系统存储之一。|  
  
## <a name="findvalue-attribute"></a>findValue 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|String|值取决于搜索的字段（由 X509FindType 属性指定）。 例如，如果搜索指纹，则此值必须为十六进制数字字符串。|  
  
## <a name="x509findtype-attribute"></a>x509FindType 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|枚举|值包括：FindByThumbprint、 FindBySubjectName、 FindBySubjectDistinguishedName、 FindByIssuerName、 FindByIssuerDistinguishedName、 FindBySerialNumber、 FindByTimeValid、 FindByTimeNotYetValid、 FindBySerialNumber、 FindByTimeExpired、 FindByTemplateNameFindByApplicationPolicy、 FindByCertificatePolicy、 FindByExtension、 FindByKeyUsage、 和 FindBySubjectKeyIdentifier。|  
  
## <a name="storelocation-attribute"></a>storeLocation 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|枚举|CurrentUser 或 LocalMachine。|  
  
## <a name="storename-attribute"></a>storeName 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|枚举|值包括：AddressBook、 AuthRoot、 CertificateAuthority、 Disallowed、 My、 根、 TrustedPeople 和 TrustedPublisher。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<scopedCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|表示特定服务为身份验证提供的 X.509（作用域）证书的集合。|  
  
## <a name="remarks"></a>备注  
 此元素使客户端能够根据与它通信的服务的 URL 来配置要使用的服务证书。 这在已颁发令牌的方案中尤其有用，在这些方案中，客户端可与多个服务（终端服务以及中间的安全令牌服务）进行通信。 对于使用基于证书的消息安全的绑定，此证书用于加密发送给服务的消息，并期望服务用它来对客户端的应答进行签名。  
  
 如果绑定需要服务的证书，但在 ScopedCertificates 中未找到服务 URL 的特定证书，则使用默认证书。  
  
 有关详细信息，请参阅的"作用域证书"部分[如何：创建联合客户端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)。  
  
## <a name="example"></a>示例  
 下面的示例向集合中添加一个 X.509 证书。  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>
- <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>
- [如何：创建联合客户端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [使用证书](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [保证客户端的安全](../../../../../docs/framework/wcf/securing-clients.md)
- [保护服务和客户端的安全](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
