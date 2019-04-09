---
title: 传输安全概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 04526e8aea09b412de4d3a94f17938b02ad6527b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105269"
---
# <a name="transport-security-overview"></a>传输安全概述
Windows Communication Foundation (WCF) 中的传输安全机制取决于绑定和正在使用的传输。 例如，当使用 <xref:System.ServiceModel.WSHttpBinding> 类时，传输为 HTTP，保证传输安全的主要机制为 HTTP 上的安全套接字层 (SSL) （通常称为 HTTPS）。 本主题讨论 WCF 系统提供绑定中使用的主要传输安全机制。  
  
> [!NOTE]
>  使用 SSL 安全时使用.NET Framework 3.5 及更高版本的 WCF 客户端在其证书存储中使用这两个中间证书和 SSL 协商，以在服务上执行证书链验证期间收到的中间证书证书。 .NET Framework 3.0 仅使用本地证书存储区中安装的中间证书。  
  
> [!WARNING]
>  在使用传输安全时，可能会覆盖 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 属性。 若要避免这种情况的发生集<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType>到<xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>。 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 是一个服务行为，可以设置对服务说明。  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 默认情况下，<xref:System.ServiceModel.BasicHttpBinding> 类不提供安全性。 此绑定旨在提供与不实现安全机制的 Web 服务提供程序的互操作性。 但可以通过将 <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> 属性设置为 <xref:System.ServiceModel.BasicHttpSecurityMode.None> 以外的值来启用安全。 若要启用传输安全，请将该属性设置为 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>。  
  
### <a name="interoperation-with-iis"></a>与 IIS 的互操作  
 <xref:System.ServiceModel.BasicHttpBinding> 类主要用于与现有的 Web 服务和由 Internet 信息服务 (IIS) 承载的许多服务进行互操作。 因此，此绑定的传输安全旨在实现与 IIS 站点的无缝互操作。 通过将安全模式设置为 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>，然后设置客户端凭据类型可以实现这一目的。 凭据类型值对应于 IIS 目录安全机制。 下面的代码演示如何设置模式以及如何将凭据类型设置为 Windows。 当客户端和服务器在同一个 Windows 域中时，您可以使用此配置。  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 或在配置中：  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 以下几节讨论其他客户端凭据类型。  
  
#### <a name="basic"></a>Basic  
 这对应于 IIS 中的基本身份验证方法。 使用此模式时，必须为 IIS 服务器配置 Windows 用户帐户和适当的 NTFS 文件系统权限。 有关详细信息[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，请参阅[启用基本身份验证和配置领域名](https://go.microsoft.com/fwlink/?LinkId=88592)。 有关详细信息[!INCLUDE[iisver](../../../../includes/iisver-md.md)]，请参阅[IIS 7.0 Beta:配置基本身份验证](https://go.microsoft.com/fwlink/?LinkId=88593)。  
  
#### <a name="certificate"></a>证书  
 IIS 有一个要求客户端使用证书进行登录的选项。 此功能还可以使 IIS 将客户端证书映射到 Windows 帐户。 有关详细信息[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，请参阅[IIS 6.0 中启用客户端证书](https://go.microsoft.com/fwlink/?LinkId=88594)。 有关详细信息[!INCLUDE[iisver](../../../../includes/iisver-md.md)]，请参阅[IIS 7.0 Beta:在 IIS 7.0 中配置服务器证书](https://go.microsoft.com/fwlink/?LinkId=88595)。  
  
#### <a name="digest"></a>摘要  
 摘要式身份验证类似于基本身份验证，但其具有以哈希形式而不是明文形式发送凭据的优点。 有关详细信息[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，请参阅[摘要式身份验证在 IIS 6.0 中](https://go.microsoft.com/fwlink/?LinkID=88443)。 有关详细信息[!INCLUDE[iisver](../../../../includes/iisver-md.md)]，请参阅[IIS 7.0 Beta:配置摘要式身份验证](https://go.microsoft.com/fwlink/?LinkId=88596)。  
  
#### <a name="windows"></a>Windows  
 这对应于 IIS 中的集成 Windows 身份验证。 设置为此值时，还需要服务器位于使用 Kerberos 协议作为其域控制器的 Windows 域中。 如果服务器不在支持 Kerberos 的域中，或者如果 Kerberos 系统失败，您可以使用下一节中说明的 NT LAN Manager (NTLM) 值。 有关详细信息[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，请参阅[IIS 6.0 中的集成 Windows 身份验证](https://go.microsoft.com/fwlink/?LinkId=88597)。 有关详细信息[!INCLUDE[iisver](../../../../includes/iisver-md.md)]，请参阅[IIS 7.0 Beta:在 IIS 7.0 中配置服务器证书](https://go.microsoft.com/fwlink/?LinkId=88595)。  
  
#### <a name="ntlm"></a>NTLM  
 这使服务器可以在 Kerberos 协议失败时使用 NTLM 进行身份验证。 有关中配置 IIS 的详细信息[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，请参阅[强制 NTLM 身份验证](https://go.microsoft.com/fwlink/?LinkId=88598)。 对于 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]，Windows 身份验证包括 NTLM 身份验证。 有关详细信息，请参阅[IIS 7.0 Beta:在 IIS 7.0 中配置服务器证书](https://go.microsoft.com/fwlink/?LinkID=88595)。  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> 类专用于与实现 WS* 规范的服务进行互操作。 此绑定的传输安全为 HTTP 上的安全套接字层 (SSL)，即 HTTPS。 若要创建使用 SSL 的 WCF 应用程序，请使用 IIS 承载该应用程序。 或者，如果您要创建自承载的应用程序，请使用 HttpCfg.exe 工具将 X.509 证书绑定到计算机上的特定端口。 作为 WCF 应用程序作为终结点地址的一部分指定端口号。 使用传输模式时，终结点地址必须包括 HTTPS 协议，否则运行时将引发异常。 有关详细信息，请参阅[HTTP 传输安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)。  
  
 对于客户端身份验证，请将 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 类的 <xref:System.ServiceModel.HttpTransportSecurity> 属性设置为 <xref:System.ServiceModel.HttpClientCredentialType> 枚举值之一。 枚举值与 <xref:System.ServiceModel.BasicHttpBinding> 的客户端凭据类型等同，并由 IIS 服务承载。  
  
 下面的示例演示与 Windows 的客户端凭据类型一起使用的绑定。  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 此绑定只提供消息级别的安全，不提供传输级别的安全。  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> 类使用 TCP 进行消息传输。 通过实现 TCP 上的传输层安全性 (TLS) 为传输模式提供安全。 由操作系统提供 TLS 实现。  
  
 也可以通过将 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> 类的 <xref:System.ServiceModel.TcpTransportSecurity> 属性设置为 <xref:System.ServiceModel.TcpClientCredentialType> 值之一来指定客户端的凭据类型，如下面的代码所示。  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>客户端  
 在客户端，必须使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 类的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法指定证书。  
  
> [!NOTE]
>  如果您要使用 Windows 安全性，则不需要证书。  
  
 下面的代码使用唯一标识证书的证书指纹。 有关证书的详细信息，请参阅[使用证书](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 或者，在客户端的配置中指定的证书使用[ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)的行为部分中的元素。  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 <xref:System.ServiceModel.NetNamedPipeBinding> 类用于进行有效的计算机内通信；也就是说，虽然可以在同一网络上的两台计算机之间创建命名管道通道，但进程是在同一台计算机上运行的。 此绑定只提供传输级别的安全。 在创建使用此绑定的应用程序时，终结点地址必须包括“net.pipe”作为终结点地址的协议。  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 使用传输安全时，此绑定与已颁发的令牌 (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>) 一起使用 HTTP 上的 SSL（称为 HTTPS）。 联合身份验证应用程序的详细信息，请参阅[联合身份验证和颁发令牌](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> 类是旨在使用对等网络功能进行有效通信的一种安全传输。 TCP 是协议，这与类和绑定的名称相一致。 当安全模式设置为“传输”时，绑定将实现 TCP 上的 TLS。 有关对等功能的详细信息，请参阅[对等网络](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding 和 NetMsmqBinding  
 有关传输的完整讨论安全与消息队列 （以前称为 MSMQ），请参阅[使用传输安全保护消息](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)。  
  
## <a name="see-also"></a>请参阅

- [WCF 安全编程](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
