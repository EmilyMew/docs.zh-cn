---
title: <wsFederation>
ms.date: 03/30/2017
ms.assetid: c537f770-68bd-4f82-96ad-6424ad91369f
author: BrucePerlerMS
ms.openlocfilehash: de79ad6447fe67afc596783eff3fa3e6a02b600c
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654583"
---
# <a name="wsfederation"></a>\<wsFederation>
提供配置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM)。  
  
\<system.identityModel.services>  
\<federationConfiguration>  
\<wsFederation>  
  
## <a name="syntax"></a>语法  
  
```xml
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation authenticationType=xs:string (URI)  
                  freshness=xs:decimal  
                  homerealm=xs:string (URI)  
                  issuer=xs:string (URI)  
                  persistentCookiesOnPassiveRedirects=xs:boolean  
                  passiveRedirectEnabled=xs:boolean  
                  policy=xs:string (URI)  
                  realm=xs:string (URI)  
                  reply=xs:string (URI)  
                  request=xs:string (URI)  
                  requestPtr=xs:string (URI)  
                  requireHttps=xs:boolean  
                  resource=xs:string (URI)  
                  signInQueryString=xs:string  
                  signOutQueryString=xs:string  
                  signOutReply=xs:string (URL)  
    </wsFederation>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|authenticationType|一个认证类型的 URI。 设置 Ws-federation 登录请求 wauth 参数。 可选。 默认值为空字符串，指定不在请求中包括的 wauth 参数。|  
|新鲜度|身份验证请求所需的最大生存期（以分钟为单位）。 设置 Ws-federation 登录请求 wfresh 参数。 可选。 默认值为零。 可选。 **警告：** 下一版本的.NET Framework 4.5`freshness`属性的类型将为`xs:string`，其默认值将为`null`。|  
|homeRealm|标识提供者 (IdP) 用于进行身份验证主领域。 设置 Ws-federation 登录请求 whr 参数。 可选。 默认值为空字符串，指定不在请求中包括的 whr 参数。|  
|issuer|预期的令牌颁发者的 URI。 设置登录请求的基 URL 的 WS 联合身份验证和所需的注销请求。|  
|persistentCookiesOnPassiveRedirects|指定是否在身份验证颁发永久性 cookie。 可选。 默认值为"false"，不发出 cookies。|  
|passiveRedirectEnabled|指定是否启用 WSFAM 自动将未经授权的请求重定向到 STS。 可选。 默认值为"true"，未经授权的请求自动重定向。|  
|策略|指定要在登录请求中使用的相关策略的位置的 URL。 默认值为一个空字符串。 设置 Ws-federation 登录请求 wp 参数。 可选。 默认值为空字符串，指定不在请求中包括的 wp 参数。|  
|realm|请求领域的 URI。 (一个 URI，标识信赖方 (RP) 对安全令牌服务 (STS)。)设置请求 wtrealm WS 联合身份验证登录请求参数。 必需。|  
|回复|标识依赖方 (RP) 应用程序的地址的 URL 要接受来自安全标志服务 (STS) 的回复。 设置 Ws-federation 登录请求 wreply 参数。 可选。 默认值为空字符串，指定在请求中不包含 wreply 参数。|  
|请求|令牌颁发请求。 设置 Ws-federation 登录请求 wreq 参数。 可选。 默认值为空字符串，指定不在请求中包括的 wreq 参数。 在请求中不包含 wreq 或 wreqptr 参数意味着 STS 知道哪种颁发的令牌。|  
|requestPtr|指定的令牌颁发请求位置的 URL。 设置请求 wreqptr 参数。 可选。 默认值为空字符串，指定不在请求中包括的 wreqptr 参数。 在请求中不包含 wreq 或 wreqptr 参数意味着 STS 知道哪种颁发的令牌。|  
|requireHttps|指定与安全令牌服务 (STS) 的通信是否必须使用 HTTPS 协议。 可选。 默认值为"true"，则必须使用 HTTPS。|  
|Resource — 资源|标识访问的资源、依赖方 (RP)和对安全标志服务 (STS) 的 URI。 可选。 设置 Ws-federation 登录请求 wres 参数。 可选。 默认值为空字符串，指定不在请求中包括的 wres 参数。 **注意：** wres 是旧的参数。 指定`realm`属性以改为使用的 wtrealm 参数。|  
|signInQueryString|提供了一个可扩展点来 WS 联合身份验证登录请求 URL 中指定应用程序定义查询参数。 可选。 默认值为空字符串，指定应在请求中包含任何其他参数。 参数被指定为使用以下形式的查询字符串片段： `"param1=value1&param2=value2&param3=value3"` ，依此类推。 **注意：** 在配置文件 &"必须使用它的实体引用，指定查询字符串中的字符`&`。|  
|signOutQueryString|提供了一个可扩展点来 WS 联合身份验证登录请求 URL 中指定应用程序定义查询参数。 可选。 默认值为空字符串，指定应在请求中包含任何其他参数。 参数被指定为使用以下形式的查询字符串片段： `"param1=value1&param2=value2&param3=value3"` ，依此类推。 **注意：** 在配置文件 &"必须使用它的实体引用，指定查询字符串中的字符`&`。|  
|signOutReply|在被动注销通过 WS 联合身份验证协议中指定的客户端应被重定向到由安全令牌服务 (STS) 的 URL。 设置 WS 联合身份验证注销请求中的 wreply 参数。 可选。 默认值为空字符串，指定应在请求中包含任何其他参数。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|包含配置的设置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。|  
  
## <a name="remarks"></a>备注  
 可以使用`<wsFederation>`元素的 WSFAM 配置默认 WS 联合身份验证参数设置和默认行为。 WS 联合身份验证下定义的参数设置`<wsFederation>`元素设置等效属性公开的<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>类。 这些属性中保持不变 wsfam 颁发的每个请求。 您可以通过添加 WSFAM; 公开事件的事件处理程序处理请求的过程动态更改的 WS 联合身份验证参数例如，<xref:System.IdentityModel.Services.WSFederationAuthenticationModule.RedirectingToIdentityProvider>事件。 有关详细信息，请参阅的文档<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>类。  
  
 `<wsFederation>`元素表示由<xref:System.IdentityModel.Services.Configuration.WSFederationElement>类。 表示配置对象本身<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>类。 单个<xref:System.IdentityModel.Services.Configuration.WsFederationConfiguration>上设置实例<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>对象，它通过访问<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>属性，并提供 WSFAM 的配置。  
  
## <a name="example"></a>示例  
 下面的 XML 演示`<wsFederation>`指定 WSFAM 设置的元素。  
  
> [!WARNING]
>  在此示例中，WSFAM 不需要使用 HTTPS。 这是因为`requireHttps`特性，可以在`<wsFederation>`元素设置`false`。 对于大多数生产环境不被建议此设置，因为其可能存在安全风险。  
  
```xml
<wsFederation passiveRedirectEnabled="true"   
              issuer="http://localhost:15839/wsFederationSTS/Issue"   
              realm="http://localhost:50969/"   
              reply="http://localhost:50969/"   
              requireHttps="false"   
              signOutReply="http://localhost:50969/SignedOutPage.html"   
              signOutQueryString="Param1=value2&Param2=value2"   
              persistentCookiesOnPassiveRedirects="true" />
```  
  
## <a name="see-also"></a>请参阅
- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
