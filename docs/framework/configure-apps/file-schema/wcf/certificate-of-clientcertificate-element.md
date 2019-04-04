---
title: <certificate> <clientCertificate>元素
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 94241d022e8a97253100a67e2a779593861c093c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366512"
---
# <a name="certificate-of-clientcertificate-element"></a>\<证书 > 的\<clientCertificate > 元素
指定用于对消息进行签名和加密的 X.509 证书。  
  
 \<system.ServiceModel>  
\<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<clientCertificate>  
\<certificate>  
  
## <a name="syntax"></a>语法  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下几节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`findValue`|一个字符串，包含要在 X.509 证书存储中搜索的值。 此属性中包含的类型必须满足指定 X509FindType 的要求。 默认值为一个空字符串。|  
|`storeLocation`|指定客户端可用于验证服务器证书的 X.509 证书存储的位置。 包括以下有效值：<br /><br /> -LocalMachine： 分配给本地计算机的证书存储。<br />-CurrentUser： 分配给当前用户的证书存储。<br /><br /> 默认值为 LocalMachine。|  
|`storeName`|指定要打开的 X.509 证书存储区的名称。 包括以下有效值：<br /><br /> -通讯簿：其他用户的证书存储区。<br />-   AuthRoot:第三方证书颁发机构 (Ca) 证书存储区。<br />-证书颁发机构：中间证书颁发机构 (Ca) 证书存储区。<br />-不允许：已吊销证书的证书存储区。<br />-我：个人证书的证书存储区。<br />根：受信任的根证书颁发机构 (Ca) 证书存储区。<br />-TrustedPeople:直接受信任的人和资源的证书存储区。<br />-TrustedPublisher:直接受信任的发行者的证书存储区。<br /><br /> 默认值为 My。|  
|`X509FindType`|定义要执行的 X.509 搜索的类型。 包括以下有效值：<br /><br /> -FindByThumbPrint<br />-   FindBySubjectName<br />-   FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 属性中包含的类型必须满足指定 X509FindType 的要求。<br /><br /> 默认值为 FindBySubjectDistinguishedName。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a>备注  
 当服务必须事先拥有客户端的证书才能与该客户端进行安全通信时，可使用 `<certificate>` 元素。 使用双工通信模式时，会出现这种情况。 在更为典型的请求/响应模式中，客户端会将其证书包含在请求中，服务将使用该证书对发送回客户端的响应进行加密和签名。 但是，在双工通信模式中，服务没有来自客户端的请求，因此服务需要事先具有客户端的证书以确保发送到客户端的消息的安全。 因此，您必须通过带外协商来获取客户端的证书，并使用此元素指定该证书。 有关双工服务的详细信息，请参阅[如何：创建双工协定](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
## <a name="example"></a>示例  
 下面的代码指定如何在 `<authentication>` 元素中查找适当的 X.509 证书和自定义验证类型。  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>请参阅
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [安全行为](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [如何：创建使用自定义证书验证程序的服务](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [使用证书](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
