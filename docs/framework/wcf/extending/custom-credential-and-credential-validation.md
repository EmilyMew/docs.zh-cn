---
title: 自定义凭据和凭据验证
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 3b1ff700010f471a4d9be117f363083b6cbed493
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210628"
---
# <a name="custom-credential-and-credential-validation"></a>自定义凭据和凭据验证
安全性在 Windows Communication Foundation (WCF) 基于服务和客户端之间的凭据交换。 大多数安全方案均可使用常见的凭据类型来实现，如 Windows (Kerberos)、用户名和密码以及证书。 而本节中的主题针对需要使用新类型的凭据的情况说明如何处理和验证这些新类型。  
  
## <a name="in-this-section"></a>本节内容  
 [如何：创建使用自定义证书验证程序的服务](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 说明如何通过继承自定义 WCF 验证<xref:System.IdentityModel.Selectors.X509CertificateValidator>类。  
  
 [演练：创建自定义客户端和服务凭据](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 演示如何扩展<xref:System.ServiceModel.Description.ClientCredentials>和<xref:System.ServiceModel.Description.ServiceCredentials>类以容纳新凭据类型。 这是介绍如何创建自定义凭据类型的系列主题中的第一个主题。  
  
 [如何：创建自定义安全令牌提供程序](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 说明如何创建安全令牌提供程序来处理新的凭据类型并返回凭据的新令牌。 这是该系列主题中的第二个主题。  
  
 [如何：创建自定义安全令牌身份验证器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 说明如何创建自定义身份验证器来验证新的凭据类型。 这是该系列主题中的第三个主题。  
  
## <a name="reference"></a>参考  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>相关章节  
 [身份验证](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [联合令牌与颁发的令牌](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [授权](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>请参阅

- [安全性](../../../../docs/framework/wcf/feature-details/security.md)
