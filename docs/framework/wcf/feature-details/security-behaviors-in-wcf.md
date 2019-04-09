---
title: WCF 中的安全行为
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: d1bffef127fe295aa41b1287da1c7104464ae0bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180058"
---
# <a name="security-behaviors-in-wcf"></a>WCF 中的安全行为
在 Windows Communication Foundation (WCF) 行为修改运行时行为在服务级别或终结点级别。 (有关行为一般情况下，请参阅[指定服务运行时行为](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)。)*安全行为*允许控制凭据、 身份验证、 授权和审核日志。 可以通过编程或通过配置来使用行为。 本主题重点讨论如何配置下列与安全功能相关的行为：  
  
-   [\<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)。  
  
-   [\<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)。  
  
-   [\<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)。  
  
-   [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md).  
  
-   [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)，这还可以指定客户端可以访问元数据的安全终结点。  
  
## <a name="setting-credentials-with-behaviors"></a>用行为设置凭据  
 使用[ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)并[ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)若要设置的服务或客户端凭据值。 基础绑定配置决定是否必须设置凭据。 例如，如果安全模式设置为 `None`，则客户端和服务不会相互进行身份验证，并且不需要任何类型的凭据。  
  
 另一方面，服务绑定可能要求使用客户端凭据类型。 在此情况下，您可能必须使用行为来设置凭据值。 (有关可能的凭据类型的详细信息，请参阅[选择凭据类型](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)。)在某些情况下（例如，使用 Windows 凭据进行身份验证），环境会自动确定实际凭据值，而无需显式设置凭据值（除非您想要指定一组不同的凭据）。  
  
 所有服务凭据都找到的子元素[ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)。 下面的示例演示一个用作服务凭据的证书。  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"   
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a>服务凭据  
 [ \<ServiceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)包含四个子元素。 以下几节将讨论这些元素和它们的用法。  
  
### <a name="servicecertificate-element"></a>\<serviceCertificate > 元素  
 使用此元素可指定一个 X.509 证书，以供服务用来向使用消息安全模式的客户端证明自己的身份。 如果您使用的是定期续订的证书，则证书的指纹将会变更。 在此情况下，请使用主题名称作为 `X509FindType`，因为可以使用同一主题名称来重新颁发该证书。  
  
 有关使用的元素的详细信息，请参阅[如何：指定客户端凭据值](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)。  
  
### <a name="certificate-of-clientcertificate-element"></a>\<证书 > 的\<clientCertificate > 元素  
 使用[\<证书 >](../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)元素时该服务必须具有预先要与客户端进行安全通信的客户端的证书。 使用双工通信模式时，会出现这种情况。 在更为典型的请求-答复模式中，客户端会将它的证书包含在请求中，服务会使用该证书来确保它的响应安全返回客户端。 但是，双工通信模式没有请求和答复。 服务无法从通信中推断出客户端的证书，因此服务需要事先得到客户端的证书来保护发送到客户端的消息。 您必须通过带外方式来获取客户端的证书，并使用此元素指定该证书。 有关双工服务的详细信息，请参阅[如何：创建双工协定](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
### <a name="authentication-of-clientcertificate-element"></a>\<身份验证 > 的\<clientCertificate > 元素  
 [\<身份验证 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)元素允许你自定义如何对客户端进行身份验证。 可以将 `CertificateValidationMode` 属性设置为 `None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust` 或 `Custom`。 默认情况下的级别设置为`ChainTrust`，它指定每个证书都必须存在的证书以层次结构中*根颁发机构*链的顶部。 这是最安全的模式。 您还可以将此值设置为 `PeerOrChainTrust`，该值指定受信任的链中的证书以及自行颁发的证书（对等信任）都被接受。 因为不需要从受信任的证书颁发机构那里购买自行颁发的证书，所以可以在开发和调试客户端和服务时使用此值。 在部署客户端时，请改用 `ChainTrust` 值。 还可以将该值设置为 `Custom`。 当该值设置为 `Custom` 值时，您还必须将 `CustomCertificateValidatorType` 属性设置为用于验证证书的程序集和类型。 若要创建您自己的自定义验证程序，必须从 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 抽象类进行继承。  
  
### <a name="issuedtokenauthentication-element"></a>\<issuedTokenAuthentication > 元素  
 颁发的令牌方案包含三个阶段。 在第一阶段，尝试访问服务的客户端被指引到*安全令牌服务*(STS)。 然后，STS 对该客户端进行身份验证，随后向该客户端颁发一个令牌（通常是一个安全断言标记语言 (SAML) 令牌）。 接下来，客户端携带此令牌返回服务。 服务检查该令牌，以获取使其可以对该令牌并进而对该客户端进行身份验证的数据。 若要对令牌进行身份验证，安全令牌服务所使用的证书必须为该服务所知。 [ \<IssuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)元素是所有此类安全令牌服务证书的存储库。 若要添加证书，请使用[ \<knownCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。 插入[\<添加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)为每个证书，如下面的示例中所示。  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 默认情况下，必须从安全令牌服务那里获取证书。 这些“已知的”证书可以确保只有合法的客户端才能访问服务。  
  
 应使用[ \<a d >](../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)集合中的联合应用程序利用*安全令牌服务*(STS) 颁发`SamlSecurityToken`安全令牌。 当 STS 颁发安全令牌时，它可以通过将 `SamlAudienceRestrictionCondition` 添加到安全令牌中，来指定安全令牌的目标 Web 服务的 URI。 这样，通过指定应采用以下方式执行此检查，接收方 Web 服务的 `SamlSecurityTokenAuthenticator` 将能够验证颁发的安全令牌是否针对此 Web 服务：  
  
-   设置`audienceUriMode`的属性[ \<issuedTokenAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)到`Always`或`BearerKeyOnly`。  
  
-   将有效 URI 添加到此集合，以指定有效 URI 集。 若要执行此操作，插入[\<添加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md)为每个 URI  
  
 有关详细信息，请参阅 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>。  
  
 有关使用此配置元素的详细信息，请参阅[如何：联合身份验证服务上配置凭据](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。  
  
#### <a name="allowing-anonymous-cardspace-users"></a>允许匿名 CardSpace 用户  
 将 `AllowUntrustedRsaIssuers` 元素的 `<IssuedTokenAuthentication>` 属性设置为 `true`，可以显式允许任何客户端提供已用任意 RSA 密钥对签名的自行颁发的令牌。 颁发者是*不受信任*因为该密钥没有与其关联的颁发者数据。 [!INCLUDE[infocard](../../../../includes/infocard-md.md)] 用户可以创建一个自行颁发的卡，卡中包含自行提供的标识声明。 使用此功能时一定要小心。 若要使用此功能，请将 RSA 公钥视为更加安全的密码，应将其与用户名一起存储在数据库中。 在允许客户端访问服务之前，请将客户端提供的 RSA 公钥与所提供的用户名的已存储公钥进行比较，以便对该公钥进行验证。 这里假设您已建立了注册过程，用户可以通过此过程来注册他们的用户名并将其用户名与自行颁发的 RSA 公钥相关联。  
  
## <a name="client-credentials"></a>客户端凭据  
 在要求相互进行身份验证的情况下，需要使用客户端凭据使客户端通过服务的身份验证。 当客户端必须使用服务的证书来保护发送到服务的消息时，可以使用该节来指定服务证书。  
  
 您还可以将客户端配置为联合方案的一部分，以便使用来自安全令牌服务或本地令牌颁发机构颁发的令牌。 有关联合方案的详细信息，请参阅[联合身份验证和颁发令牌](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。 下可找到所有客户端凭据[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)，如下面的代码中所示。  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"     
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"   
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
#### <a name="clientcertifictate-element"></a>\<clientCertifictate > 元素  
 可以使用此元素设置用于对客户端进行身份验证的证书。 有关详细信息，请参阅[如何：指定客户端凭据值](../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)。  
  
#### <a name="httpdigest"></a>\<httpDigest>  
 必须使用 Windows 上的 Active Directory 和 Internet 信息服务 (IIS) 启用此功能。 有关详细信息，请参阅[摘要式身份验证在 IIS 6.0 中](https://go.microsoft.com/fwlink/?LinkId=88443)。  
  
#### <a name="issuedtoken-element"></a>\<issuedToken > 元素  
 [ \<IssuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)包含用于配置本地颁发者的令牌，或者使用与安全令牌服务的行为的元素。 有关配置客户端以使用本地颁发者的说明，请参阅[如何：配置本地颁发者](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)。  
  
#### <a name="localissueraddress"></a>\<localIssuerAddress>  
 指定默认的安全令牌服务地址。 使用此时<xref:System.ServiceModel.WSFederationHttpBinding>不提供安全令牌服务，或者当联合绑定的颁发者地址的 URL`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`或`null`。 在这些情况下，必须使用本地颁发机构的地址和用来与该颁发机构进行通信的绑定来配置 <xref:System.ServiceModel.Description.ClientCredentials>。  
  
#### <a name="issuerchannelbehaviors"></a>\<issuerChannelBehaviors>  
 使用[ \<issuerChannelBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)添加与安全令牌服务通信时使用的 WCF 客户端行为。 定义中的客户端行为[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)部分。 若要使用已定义的行为，添加 <`add`> 元素`<issuerChannelBehaviors>`具有两个属性的元素。 将 `issuerAddress` 设置为安全令牌服务的 URL，将 `behaviorConfiguration` 特性设置为已定义终结点行为的名称，如下面的示例所示。  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />     
```  
  
#### <a name="servicecertificate-element"></a>\<serviceCertificate > 元素  
 使用此元素可控制服务证书的身份验证。  
  
 [ \<DefaultCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)元素可以存储在该服务不指定任何证书时使用单个证书。  
  
 使用[ \<scopedCertificates >](../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)并[\<添加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)设置与特定服务关联的服务证书。 `<add>` 元素包含一个 `targetUri` 属性，该属性用于将证书与服务相关联。  
  
 [\<身份验证 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)元素指定用于对证书进行身份验证的信任级别。 默认情况下，该级别设置为“ChainTrust”，它指定每个证书都必须存在于某个证书层次结构中，而该层次结构以位于证书链顶端的受信任的证书颁发机构结束。 这是最安全的模式。 还可以将此值设置为“PeerOrChainTrust”，该值指定受信任的链中的证书以及自行颁发的证书（对等信任）都被接受。 因为不需要从受信任的证书颁发机构那里购买自行颁发的证书，所以可以在开发和调试客户端和服务时使用此值。 在部署客户端时，请改用“ChainTrust”值。 还可以将此值设置为“Custom”或“None”。 若要使用“Custom”值，您还必须将 `CustomCertificateValidatorType` 属性设置为用于验证证书的程序集和类型。 若要创建您自己的自定义验证程序，必须从 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 抽象类进行继承。 有关详细信息，请参阅[如何：创建使用自定义证书验证程序的服务](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)。  
  
 [\<身份验证 >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)元素包含`RevocationMode`的特性，指定如何检查证书是否已吊销。 默认值为“online”，指示自动检查证书是否已吊销。 有关详细信息，请参阅[Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
## <a name="serviceauthorization"></a>ServiceAuthorization  
 [ \<ServiceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)元素包含会影响授权、 自定义角色提供程序和模拟的元素。  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> 类被应用于服务方法。 该属性指定在授权使用受保护方法时要使用的用户组。 默认值为“UseWindowsGroups”，该值指定在 Windows 组（例如，“Administrators”或“Users”）中搜索试图访问某个资源的标识。 此外可以指定"UseAspNetRoles"以使用的自定义角色提供程序下配置 <`system.web` > 元素，如下面的代码中所示。  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"   
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add   
          name="SqlProvider"   
          type="System.Web.Security.SqlMembershipProvider"   
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 下面的代码演示与 `roleProviderName` 特性一起使用的 `principalPermissionMode`。  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">          
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"   
                        roleProviderName ="SqlProvider" />  
</behavior>   
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a>配置安全审核  
 使用[ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)指定日志写入，以及要记录的事件类型。 有关详细信息，请参阅[审核](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)。  
  
```xml  
<system.serviceModel>  
<serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a>安全元数据交换  
 对于服务和客户端开发人员来讲，向客户端导出元数据是很方便的，因为使用该操作可以下载配置和客户端代码。 为了降低服务被恶意使用者滥用的可能性，可以使用 SSL over HTTP (HTTPS) 机制来确保传输的安全。 为此，必须首先将一个适合的 X.509 证书绑定到承载该服务的计算机上的特定端口。 (有关详细信息，请参阅[Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。)其次，添加[ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md)到的服务配置并设置`HttpsGetEnabled`归于`true`。 最后，将 `HttpsGetUrl` 属性设置为服务元数据终结点的 URL，如下面的示例所示。  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>请参阅

- [审核](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Windows Server App Fabric 的安全模型](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
