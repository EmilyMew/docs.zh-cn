---
title: 重写服务标识以便进行身份验证
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d613a22b-07d7-41a4-bada-1adc653b9b5d
ms.openlocfilehash: a5a32220ad1f638bf2e93051e9b436d8270aec2f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082186"
---
# <a name="overriding-the-identity-of-a-service-for-authentication"></a>重写服务标识以便进行身份验证
通常情况下不需要设置服务上的标识，因为客户端凭据类型的选择即规定了服务元数据中公开的标识的类型。 例如，下面的配置代码使用[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)元素并设置`clientCredentialType`属性到 Windows。  

 下面的 Web 服务描述语言 (WSDL) 片断演示前面定义的终结点的标识。 在此示例中，在服务作为自承载服务的特定用户帐户下运行 (username@contoso.com)，因此用户主体名称 (UPN) 标识包含帐户名称。 在 Windows 域中，UPN 也称为用户登录名。  

 有关演示标识设置的示例应用程序，请参阅[服务标识示例](../../../../docs/framework/wcf/samples/service-identity-sample.md)。 有关服务标识的详细信息，请参阅[服务标识和身份验证](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。  
  
## <a name="kerberos-authentication-and-identity"></a>Kerberos 身份验证和标识  
 默认情况下，当服务配置为使用 Windows 凭据， [\<标识 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)元素，其中包含[ \<userPrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/userprincipalname.md)或[ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md)在 WSDL 中生成元素。 如果服务下运行`LocalSystem`， `LocalService`，或`NetworkService`帐户、 服务主体名称 (SPN) 形式的默认情况下生成`host/` \<*主机名*> 因为这些帐户有权访问计算机的 SPN 数据。 如果服务正在其他帐户下，Windows Communication Foundation (WCF) 中的窗体生成 UPN \<*用户名*>@<*domainName* `>`. 发生这种情况的原因是 Kerberos 身份验证要求向客户端提供 UPN 或 SPN，以便对服务进行身份验证。  
  
 您还可以使用 Setspn.exe 工具向域中服务的帐户注册其他 SPN。 然后，可以使用该 SPN 作为服务的标识。 若要下载该工具，请参阅[Windows 2000 资源工具包工具：Setspn.exe](https://go.microsoft.com/fwlink/?LinkId=91752)。 有关工具的详细信息，请参阅[Setspn 概述](https://go.microsoft.com/fwlink/?LinkId=61374)。  
  
> [!NOTE]
>  若要使用不带协商的 Windows 凭据类型，服务的用户帐户必须有权访问向 Active Directory 域注册的 SPN。 可以使用下列方式来实现：  
  
-   使用 NetworkService 或 LocalSystem 帐户运行服务。 因为这些帐户有权访问的计算机加入 Active Directory 域时，将建立计算机 SPN，WCF 会自动在服务的元数据 (WSDL) 中生成服务的终结点内正确的 SPN 元素。  
  
-   使用任意 Active Directory 域帐户运行服务。 在这种情况下，需要为该域帐户建立一个 SPN，这可以使用 Setspn.exe 实用工具来完成。 一旦创建该服务的帐户的 SPN，配置 WCF，以将该 SPN 发布到服务的客户端通过其元数据 (WSDL)。 这可以通过为公开的终结点设置终结点标识（借助于应用程序配置文件或代码）来完成。  
  
 有关 Spn 的详细信息，Kerberos 协议和 Active Directory，请参阅[Kerberos 技术补充程序用于 Windows](https://go.microsoft.com/fwlink/?LinkId=88330)。  
  
### <a name="when-spn-or-upn-equals-the-empty-string"></a>当 SPN 或 UPN 等于空字符串时  
 如果将 SPN 或 UPN 设置为等于空字符串，将出现多种不同的情况，具体取决于所使用的安全级别和身份验证模式：  
  
-   如果使用传输级安全，则会选择 NT LanMan (NTLM) 身份验证。  
  
-   如果使用消息级安全，则根据身份验证模式的不同，身份验证可能会失败：  
  
-   如果使用 `spnego` 模式，并且 `AllowNtlm` 属性设置为 `false`，则身份验证将失败。  
  
-   在使用 `spnego` 模式并且 `AllowNtlm` 属性设置为 `true` 的情况下，如果 UPN 为空，则身份验证将失败；如果 SPN 为空，则身份验证将成功。  
  
-   如果使用 Kerberos direct（也称为“一次完成”），则身份验证将失败。  
  
### <a name="using-the-identity-element-in-configuration"></a>使用\<标识 > 配置中的元素  
 如果将前面演示的绑定中的客户端凭据类型更改为证书`,`，则生成的 WSDL 将包含一个 Base64 序列化 X.509 证书作为标识值，如下面的代码所示。 这是除 Windows 之外的所有客户端凭据类型的默认值。  

 可以更改默认服务标识的值，也可以使用更改的标识的类型 <`identity`> 元素中配置或代码中设置标识。 下面的配置代码使用值 `contoso.com` 设置域名系统 (DNS) 标识。  

### <a name="setting-identity-programmatically"></a>以编程方式设置标识  
 你的服务无需显式指定标识，因为 WCF 会自动确定。 但是，WCF 允许您终结点上指定标识必要。 下面的代码使用特定的 DNS 标识添加了一个新的服务终结点。  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="see-also"></a>请参阅

- [如何：创建自定义客户端标识验证工具](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [服务标识和身份验证](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
