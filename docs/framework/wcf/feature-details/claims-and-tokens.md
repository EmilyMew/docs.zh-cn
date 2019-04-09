---
title: 声明和令牌
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], and tokens
ms.assetid: eff167f3-33f8-483d-a950-aa3e9f97a189
ms.openlocfilehash: 223b86310d90c877df15a99c90a0a72ea780734a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076258"
---
# <a name="claims-and-tokens"></a>声明和令牌
本主题介绍 Windows Communication Foundation (WCF) 从它支持的默认令牌创建的各种声明类型。  
  
 可以使用 <xref:System.IdentityModel.Claims.ClaimSet> 和 <xref:System.IdentityModel.Claims.Claim> 类来检查客户端凭据的声明。 `ClaimSet` 包含 `Claim` 对象的集合。 每个 `Claim` 都具有以下重要成员：  
  
-   <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 属性返回的统一资源标识符 (URI) 指定了所做声明的类型。 例如，声明类型可以是 URI 的情况是在其中的证书的指纹`http://schemas.microsoft.com/ws/20005/05/identity/claims/thumprint`。  
  
-   <xref:System.IdentityModel.Claims.Claim.Right%2A> 属性返回的 URI 指定了声明权限。 预定义的权限位于 <xref:System.IdentityModel.Claims.Rights> 类中（<xref:System.IdentityModel.Claims.Rights.Identity%2A>、<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>）。  
  
-   <xref:System.IdentityModel.Claims.Claim.Resource%2A> 属性返回与声明关联的资源。  
  
 此外，每个 <xref:System.IdentityModel.Claims.ClaimSet> 还包含一个 <xref:System.IdentityModel.Claims.ClaimSet.Issuer%2A> 属性，以表示 <xref:System.IdentityModel.Claims.ClaimSet> 的 `Issuer`。  
  
## <a name="windows-accounts"></a>Windows 帐户  
 在客户端凭据映射到 Windows 用户帐户的情况下，生成的 <xref:System.IdentityModel.Claims.ClaimSet> 具有以下值：  
  
-   `Issuer` 是 <xref:System.IdentityModel.Claims.ClaimSet> 类的静态 Windows 属性返回的值。  
  
-   集合中的声明包括：  
  
    -   <xref:System.IdentityModel.Claims.Claim> 值为安全标识符 (SID)、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 属性值为 <xref:System.IdentityModel.Claims.Claim.Right%2A> 以及返回实际 SID 值的 `Identity` 的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。 SID 是域控制器颁发给每个用户的一个唯一值。 SID 用于在与 Windows 安全交互时标识用户。  
  
    -   <xref:System.IdentityModel.Claims.Claim> 值为 SID、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 为 <xref:System.IdentityModel.Claims.Claim.Right%2A> 以及 `PossessProperty` 为 SID 值的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。  
  
    -   <xref:System.IdentityModel.Claims.Claim> 为 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>、<xref:System.IdentityModel.Claims.ClaimTypes.Name%2A> 为 <xref:System.IdentityModel.Claims.Claim.Right%2A> 以及 `PossessProperty` 为包含用户名的字符串（如“MYMACHINE\Bob”）的 <xref:System.IdentityModel.Claims.Claim.Resource%2A>。  
  
    -   用户所属的各个组的 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 的附加 SID 声明。  
  
## <a name="certificates"></a>证书  
 在客户端凭据为证书的情况下，生成的 <xref:System.IdentityModel.Claims.ClaimSet> 具有以下各值：  
  
-   对于自行颁发的证书，`Issuer` 为 <xref:System.IdentityModel.Claims.ClaimSet> 本身。 <xref:System.IdentityModel.Claims.ClaimSet> 返回 <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> 的 <xref:System.IdentityModel.Claims.ClaimTypes.Thumbprint%2A>、<xref:System.IdentityModel.Claims.Claim.Right%2A> 的 `Identity` 以及 <xref:System.IdentityModel.Claims.Claim.Resource%2A> 值，该值是一个包含证书指纹的 <xref:System.Byte> 数组。  
  
-   对于证书颁发机构颁发的证书，颁发者为表示证书颁发机构的证书的 `ClaimSet`。  
  
-   集合中的 `Claims` 包括：  
  
    -   `Claim` 为 Thumbprint、`ClaimType` 为 PossessProperty 以及 `Right` 为包含证书指纹的字节数组的 `Resource`  
  
    -   各种类型的其他 PossessProperty 声明，包括表示各种证书属性的 X500DistinguishedName、Dns、Name、Upn 和 Rsa。 Rsa 声明的资源是与证书关联的公钥。**注意**客户端凭据类型所在的证书，该服务将映射到 Windows 帐户，两个`ClaimSet`对象生成。 第一个对象包含与 Windows 帐户相关的所有声明，第二个对象包含与证书相关的所有声明。  
  
## <a name="user-namepassword"></a>用户名/密码  
 在客户端凭据是未映射到 Windows 帐户的用户名/密码（或等效项）的情况下，生成的 `ClaimSet` 由 <xref:System.IdentityModel.Claims.ClaimSet.System%2A> 类的静态 `ClaimSet` 属性颁发。 `ClaimSet`包含`Identity`声明类型的<xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>、 资源为客户端提供用户名。 对应声明的 `Right` 为 `PossessProperty`。  
  
## <a name="rsa-keys"></a>RSA 密钥  
 在使用不与证书关联的 RSA 密钥，从而`ClaimSet`自行颁发并且包含`Identity`声明类型的<xref:System.IdentityModel.Claims.ClaimTypes.Rsa%2A>、 资源为 RSA 密钥。 对应声明的 `Right` 为 `PossessProperty`。  
  
## <a name="saml"></a>SAML  
 在客户端使用安全断言标记语言 (SAML) 令牌进行身份验证的情况下，生成的 `ClaimSet` 由已对 SAML 令牌进行签名的实体来颁发，通常为颁发了 SAML 令牌的安全令牌服务 (STS) 的证书。 `ClaimSet` 中包含 SAML 令牌中的各种声明。 如果 SAML 令牌包含非 `SamlSubject` 名称的 `null`，则会创建一个类型为 `Identity`、资源类型为 <xref:System.IdentityModel.Claims.ClaimTypes.NameIdentifier%2A> 的 <xref:System.IdentityModel.Tokens.SamlNameIdentifierClaimResource> 声明。  
  
## <a name="identity-claims-and-servicesecuritycontextisanonymous"></a>标识声明和 ServiceSecurityContext.IsAnonymous  
 如果没有`ClaimSet`从客户端凭据生成的对象包含的声明`Right`的`Identity,`则<xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>属性返回`true`。 如果存在一个或多个此类声明，则 `IsAnonymous` 属性将返回 `false`。  
  
## <a name="see-also"></a>请参阅

- <xref:System.IdentityModel.Claims.ClaimSet>
- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.Rights>
- <xref:System.IdentityModel.Claims.ClaimTypes>
- [使用标识模型管理声明和授权](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
