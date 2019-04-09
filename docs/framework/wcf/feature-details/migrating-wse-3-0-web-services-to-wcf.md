---
title: 将 WSE 3.0 Web 服务迁移到 WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: a691e8f63e34f60f26d1a96a975dbe062bd59c96
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180604"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>将 WSE 3.0 Web 服务迁移到 WCF
WSE 3.0 Web 服务迁移到 Windows Communication Foundation (WCF) 的优点包括改进的性能，支持其他传输、 额外的安全方案和 WS-* 规范。 从 WSE 3.0 迁移到 WCF Web 服务可能会遇到最多 200%到 400%性能改进。 有关 wcf 支持的传输协议的详细信息，请参阅[选择传输](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。 有关 WCF 支持的方案的列表，请参阅[常用安全方案](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。 有关 WCF 支持的规范的列表，请参阅[Web 服务协议互操作性指南](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)。  
  
 以下各节提供有关如何将 WSE 3.0 Web 服务的特定功能迁移到 WCF 的指导。  
  
## <a name="general"></a>常规  
 WSE 3.0 和 WCF 应用程序包括网络级互操作性和一组通用的术语。 WSE 3.0 和 WCF 应用程序进行网络级互操作基于集的 WS-* 规范，它们都支持。 在开发 WSE 3.0 或 WCF 应用程序时没有一组通用的术语，例如，WSE 和身份验证模式中的关守安全断言的名称。  
  
 尽管有许多相似方面之间的 WCF 和 ASP.NET 或 WSE 3.0 编程模型，它们是不同。 WCF 编程模型的详细信息，请参阅[基本编程生命周期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)。  
  
> [!NOTE]
>  若要将 WSE Web 服务迁移到 WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具可用于生成客户端。 另一方面，该客户端还包含可以用作 WCF 服务起点的接口和类。 所生成的接口将 <xref:System.ServiceModel.OperationContractAttribute> 属性 (attribute) 应用于将 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 属性 (property) 设置为 `*` 的协定的成员。 当 WSE 客户端调用 Web 服务时使用此设置时，会引发以下异常：**Web.Services3.ResponseProcessingException:WSE910:响应消息的处理过程中发生错误，你可以在内部异常中找到错误**。 若要缓解此问题，可以将 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 属性 (attribute) 的 <xref:System.ServiceModel.OperationContractAttribute> 属性 (property) 设置为非 `null` 值，例如 `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`。  
  
## <a name="security"></a>安全性  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>使用策略文件保护其安全的 WSE 3.0 Web 服务  
 WCF 服务可以使用配置文件来保护服务，该机制与 WSE 3.0 策略文件相似。 在 WSE 3.0 中，当使用策略文件来保护 Web 服务的安全时，可以使用关守安全断言或自定义策略断言。 关守安全断言严格映射到 WCF 安全绑定元素的身份验证模式。 不只 WCF 身份验证模式和 WSE 3.0 关守安全断言名称相同或类似地，确保使用相同的凭据类型消息的安全。 例如，`usernameForCertificate`在 WSE 3.0 关守安全断言映射到`UsernameForCertificate`WCF 中的身份验证模式。 下面的代码示例演示如何使用的最小策略`usernameForCertificate`在 WSE 3.0 关守安全断言映射到`UsernameForCertificate`在 WCF 自定义绑定中的身份验证模式。  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 若要迁移到 WCF 策略文件中指定的 WSE 3.0 Web 服务的安全设置，自定义绑定必须创建配置文件中，并且必须将关守安全断言设置为其等效的身份验证模式。 此外，当 WSE 3.0 客户端与服务进行通信时，必须将自定义绑定配置为使用 2004 年 8 月版 WS-Addressing 规范。 当已迁移的 WCF 服务不需要与 WSE 3.0 客户端的通信，并且必须保持同等安全性，请考虑使用具有适当的安全设置，而不是创建自定义绑定的 WCF 系统定义绑定。  
  
 下表列出了 WSE 3.0 策略文件和 WCF 中等效的自定义绑定之间的映射。  
  
|WSE 3.0 关守安全断言|WCF 自定义绑定配置|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 有关在 WCF 中创建自定义绑定的详细信息，请参阅[自定义绑定](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>使用应用程序代码保护其安全的 WSE 3.0 Web 服务  
 使用 WSE 3.0 还是使用 WCF，可以应用程序代码而不是在配置中指定的安全要求。 在 WSE 3.0 中，可以通过以下方法完成此工作：创建一个派生自 `Policy` 类的类，然后通过调用 `Add` 方法添加相应的要求。 有关在代码中指定的安全要求的更多详细信息，请参阅[如何：Web 服务安全而无需使用策略文件](https://go.microsoft.com/fwlink/?LinkId=73747)。 在 WCF 中，若要在代码中指定安全要求，创建的实例<xref:System.ServiceModel.Channels.BindingElementCollection>类，并添加的实例<xref:System.ServiceModel.Channels.SecurityBindingElement>到<xref:System.ServiceModel.Channels.BindingElementCollection>。 使用 <xref:System.ServiceModel.Channels.SecurityBindingElement> 类的静态身份验证模式帮助器方法来设置安全断言需求。 有关使用 WCF 在代码中指定安全要求的更多详细信息，请参阅[如何：创建自定义绑定使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)和[如何：为指定的身份验证模式创建 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 自定义策略断言  
 在 WSE 3.0 中，有两种类型的自定义策略断言：保护 SOAP 消息安全的策略断言和不保护 SOAP 消息安全的策略断言。 保护 SOAP 消息安全的策略断言派生自 WSE 3.0`SecurityPolicyAssertion`类，并在 WCF 中在概念上的等效是<xref:System.ServiceModel.Channels.SecurityBindingElement>类。  
  
 请注意一个重要特点是 WSE 3.0 关守安全断言是 WCF 身份验证模式的子集。 如果已在 WSE 3.0 中创建自定义策略断言，可能有等效的 WCF 身份验证模式。 例如，WSE 3.0 没有提供与 `UsernameOverTransport` 关守安全断言等效的 CertificateOverTransport 安全断言，但使用 X.509 证书进行客户端身份验证。 如果已定义这种情况下你自己的自定义策略断言，则 WCF 会使迁移非常简单。 WCF 定义此方案中，身份验证模式，因此可以充分利用静态身份验证模式帮助器方法来配置 WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>。  
  
 当没有为 WCF 身份验证模式，相当于保护 SOAP 消息安全的自定义策略断言时，派生一个类从<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>，<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>或<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF 类并指定等效的绑定元素。 有关更多详细信息，请参阅[如何：创建自定义绑定使用 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)。  
  
 若要转换不保护 SOAP 消息的自定义策略断言，请参阅[Filtering](../../../../docs/framework/wcf/feature-details/filtering.md)示例和示例[自定义消息拦截器](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 自定义安全令牌  
 用于创建自定义令牌的 WCF 编程模型是与 WSE 3.0 不同。 有关在 WSE 中创建自定义令牌的详细信息，请参阅[创建自定义安全令牌](https://go.microsoft.com/fwlink/?LinkID=73750)。 有关在 WCF 中创建自定义令牌的详细信息，请参阅[如何：创建自定义令牌](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 自定义令牌管理器  
 用于创建自定义令牌管理器的编程模型与 WSE 3.0 WCF 不同。 有关如何创建自定义令牌管理器和其他组件所需的自定义安全令牌的详细信息，请参阅[如何：创建自定义令牌](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。  
  
> [!NOTE]
>  如果已创建自定义`UsernameToken`安全令牌管理器中，WCF 提供了一个简单的机制来指定比创建自定义安全令牌管理器的身份验证逻辑。 有关更多详细信息，请参阅[如何：使用自定义用户名和密码验证程序](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>使用 MTOM 编码 SOAP 消息的 WSE 3.0 Web 服务  
 像 WSE 3 应用程序，WCF 应用程序可以指定 MTOM 消息编码配置中。 若要迁移此设置，将添加[ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md)为该服务的绑定。 下面的代码示例演示如何指定 MTOM 编码 WSE 3.0 中的等效 WCF 中的服务。  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>消息  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>使用 WSE 消息 API 的 WSE 3.0 应用程序  
 当使用 WSE 消息 API 来获取对在客户端和服务之间交换的 XML 的直接访问时，可以将应用程序转换为使用“Plain Old XML”(POX)。 有关 POX 的更多详细信息，请参阅[POX 应用程序与互操作性](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md)。 有关 WSE 消息 API 的更多详细信息，请参阅[发送和接收 SOAP 消息使用 WSE 消息 API](https://go.microsoft.com/fwlink/?LinkID=73755)。  
  
## <a name="transports"></a>传输  
  
### <a name="tcp"></a>TCP  
 默认情况下，WSE 3.0 客户端和 Web 服务发送 SOAP 消息使用 TCP 传输的不进行互操作与 WCF 客户端和 Web 服务。 这一不兼容性是由于 TCP 协议中使用的组帧存在差异以及性能方面的原因。 但是，WCF 示例详细介绍了如何实现与 WSE 3.0 进行互操作的自定义 TCP 会话。 有关此示例的详细信息，请参阅[传输：WSE 3.0 TCP 互操作性](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)。  
  
 若要指定 WCF 应用程序使用 TCP 传输，请使用[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。  
  
### <a name="custom-transport"></a>自定义传输协议  
 WCF 中的 WSE 3.0 自定义传输的等效项是通道扩展。 有关创建通道扩展的详细信息，请参阅[扩展通道层](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)。  
  
## <a name="see-also"></a>请参阅

- [基本编程生命周期](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [自定义绑定](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [如何：使用 SecurityBindingElement 创建自定义绑定](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [如何：为指定的身份验证模式创建 SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
