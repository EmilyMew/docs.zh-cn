---
title: 对 WCF 使用多个身份验证方案
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: b0f5da9a4c6fdfede9a86434f49f9e9821778176
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102305"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>对 WCF 使用多个身份验证方案
WCF 现在允许您对单个终结点上指定多个身份验证方案。 此外，Web 承载的服务可以直接从 IIS 继承其身份验证设置。 自承载服务可以指定可使用的身份验证方案。 有关在 IIS 中设置身份验证设置的详细信息，请参阅[IIS 身份验证](https://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>承载于 IIS 中的服务  
 对于承载于 IIS 中的服务，设置您希望在 IIS 中使用的身份验证方案。 然后在你的服务的 web.config 文件中，在绑定配置客户端凭据类型指定为"InheritedFromHost"以下 XML 代码段中所示：  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 您可以指定仅希望将一部分的身份验证方案，可与你的服务使用 ServiceAuthenticationBehavior 或\<serviceAuthenticationManager > 元素。 在代码中对此进行配置时，使用 ServiceAuthenticationBehavior，如下面的 XML 代码段中所示。  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 在配置此配置文件中时，使用\<serviceAuthenticationManager > 元素，如以下 XML 代码段中所示。  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 这将确保只有一部分此处列出的身份验证方案将被考虑应用于服务终结点，具体是哪些身份验证方案取决于 IIS 中所选的内容。 这意味着，开发人员可以通过从 serviceAuthenticationManager 列表中省略基本身份验证而从列表中排除它，甚至即使在 IIS 中启用基本身份验证，它也将不会在服务终结点上应用  
  
## <a name="self-hosted-services"></a>自承载服务  
 自承载服务在配置上稍有不同，因为没有要从其继承设置的 IIS。 在本例中使用\<serviceAuthenticationManager > 元素或 ServiceAuthenticationBehavior 指定将继承的身份验证设置。 在代码中如下所示：  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 在配置中如下所示：  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 然后，你可以在绑定设置中指定 InheritFromHost，如下面的 XML 代码段中所示。  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 或者，你可以通过在 HTTP 传输绑定元素上设置身份验证架构，在自定义绑定中指定身份验证架构，如下面的配置代码段所示。  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>请参阅

- [绑定与安全](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [终结点：地址、绑定和协定](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [配置系统提供的绑定](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [使用自定义绑定的安全功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [绑定](../../../../docs/framework/wcf/feature-details/bindings.md)
- [自定义绑定](../../../../docs/framework/wcf/extending/custom-bindings.md)
