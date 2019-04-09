---
title: 如何：配置本地颁发者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
ms.openlocfilehash: cb4a2bcc6f62fac5d0dde82ab32ed6e04e8a9b7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095550"
---
# <a name="how-to-configure-a-local-issuer"></a>如何：配置本地颁发者
本主题说明如何配置客户端以便为已颁发令牌使用本地颁发者。  
  
 当客户端与联合服务通信时，服务端通常指定安全令牌服务的地址，客户端需要该安全令牌服务来颁发客户端用于向联合服务对自己进行身份验证的令牌。 在某些情况下，客户端可能会将配置为使用*本地颁发者*。  
  
 Windows Communication Foundation (WCF) 在联合绑定的颁发者地址的情况下使用本地颁发者`http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`或`null`。 在这样的情况下，必须使用本地颁发者的地址和要使用的绑定来配置 <xref:System.ServiceModel.Description.ClientCredentials>，这样才能与该颁发者通信。  
  
> [!NOTE]
>  如果<xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A>的属性`ClientCredentials`类设置为`true`、 未指定本地颁发者地址，并通过指定的颁发者地址[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)或其他联合的绑定是`http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self`， `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous`，或者`null`，然后 Windows[!INCLUDE[infocard](../../../../includes/infocard-md.md)]使用颁发者。  
  
### <a name="to-configure-the-local-issuer-in-code"></a>在代码中配置本地颁发者  
  
1.  创建类型的变量 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2.  将该变量设置为从 <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> 类的 `ClientCredentials` 属性返回的实例。 该实例由客户端的 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 属性（继承自 <xref:System.ServiceModel.ClientBase%601>）或 <xref:System.ServiceModel.ChannelFactory.Credentials%2A> 的 <xref:System.ServiceModel.ChannelFactory> 属性返回：  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  将 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> 属性设置为 <xref:System.ServiceModel.EndpointAddress> 的一个新实例，将本地颁发者的地址作为传递给构造函数的自变量。  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     或者，创建一个新的 <xref:System.Uri> 实例作为传递给构造函数的自变量。  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     `addressHeaders`参数是一个数组<xref:System.ServiceModel.Channels.AddressHeader>实例，如所示。  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  设置本地颁发者使用的绑定<xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A>属性。  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  可选。 为本地颁发者添加已配置的终结点行为，方法是将这些行为添加到由 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> 属性返回的集合中。  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>在配置中配置本地颁发者  
  
1.  创建[ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md)的子元素[ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)是自身的子级的元素[ \<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)中的终结点行为元素。  
  
2.  将 `address` 属性设置为将要接收令牌请求的本地颁发者的地址。  
  
3.  将 `binding` 和 `bindingConfiguration` 属性设置为这样的值，即在与本地颁发者终结点通信时，这些值可引用要使用的适当绑定。  
  
4.  可选。 设置[\<标识 >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)的子元素 <`localIssuer`> 元素，并指定本地颁发者的标识信息。  
  
5.  可选。 设置[\<标头 >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)的子元素 <`localIssuer`> 元素，并指定正确寻址本地颁发者所需的其他标头。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 请注意，如果颁发者地址和绑定是为给定的绑定而指定的，则不对使用该绑定的终结点使用本地颁发者。 希望始终使用本地颁发者的客户端应该确保不使用这样的绑定，或修改该绑定，使颁发者地址为 `null`。  
  
## <a name="see-also"></a>请参阅

- [如何：在联合身份验证服务上配置凭据](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [如何：创建联合客户端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [如何：创建 WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
