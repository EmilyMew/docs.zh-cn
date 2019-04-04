---
title: <serviceCertificate> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: bd2d59218ce40639ac04aa7c5cc157fe37eb9937
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373798"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCertificate> of \<serviceCredentials>
指定一个 X.509 证书，以供服务用来向使用 Message 安全模式的客户端证明自己的身份。  
  
 \<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<serviceCertificate>  
  
## <a name="syntax"></a>语法  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`findValue`|一个字符串，包含要在 X.509 证书存储中搜索的值。 此属性中包含的类型必须满足指定 X509FindType 的要求。 默认值为一个空字符串。|  
|`storeLocation`|指定客户端可用于验证服务器证书的 X.509 证书存储的位置。 包括以下有效值：<br /><br /> -LocalMachine： 分配给本地计算机的证书存储。<br />-CurrentUser： 分配给当前用户的证书存储。<br /><br /> 默认值为 LocalMachine。|  
|`storeName`|指定要打开的 X.509 证书存储区的名称。 包括以下有效值：<br /><br /> -通讯簿：其他用户的证书存储区。<br />-   AuthRoot:第三方证书颁发机构 (Ca) 证书存储区。<br />-CertificatAuthority:中间证书颁发机构 (Ca) 证书存储区。<br />-不允许：已吊销证书的证书存储区。<br />-我：个人证书的证书存储区。<br />根：受信任的根证书颁发机构 (Ca) 证书存储区。<br />-TrustedPeople:直接受信任的人和资源的证书存储区。<br />-TrustedPublisher:直接受信任的发行者的证书存储区。<br /><br /> 默认值为 My。|  
|`x509FindType`|定义要执行的 X.509 搜索的类型。 包括以下有效值：<br /><br /> -FindByThumbprint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 属性中包含的类型必须满足指定 X509FindType 的要求。<br /><br /> 默认值为 FindBySubjectDistinguishedName。|  
  
### <a name="child-elements"></a>子元素  
 无  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|指定要用于对服务进行身份验证的凭据以及与客户端凭据验证相关的设置。|  
  
## <a name="remarks"></a>备注  
 使用此元素可指定一个 X.509 证书，以供服务用来向使用 Message 安全模式的客户端证明自己的身份。 如果您使用的是将会定期续订的证书，则证书的指纹将会变更。 在此情况下，请使用主题名称作为 `x509FindType`，因为可以使用同一主题名称来重新颁发该证书。  
  
 有关使用的元素的详细信息，请参阅[如何：指定客户端凭据值](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)。  
  
## <a name="see-also"></a>请参阅
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [如何：指定客户端凭据值](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [安全行为](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
