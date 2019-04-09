---
ms.openlocfilehash: ae3766e2045b5834fbf6ea20415942413b1590c0
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761271"
---
### <a name="wcf-services-that-use-nettcp-with-ssl-security-and-md5-certificate-authentication"></a>使用带有 SSL 安全和 MD5 证书身份验证的 NETTCP 的 WCF 服务

|   |   |
|---|---|
|详细信息|.NET Framework 4.6 将 TLS 1.1 和 TLS 1.2 添加到 WCF SSL 默认协议列表。 客户端和服务器计算机都安装了 .NET Framework 4.6 或更高版本时，TLS 1.2 用于协商。TLS 1.2 不支持 MD5 证书身份验证。 因此，如果客户使用 MD5 证书，WCF 客户端将无法连接到 WCF 服务。|
|建议|可以通过执行下列任一操作来解决此问题，以便 WCF 客户端可以连接 WCF 服务器：<ul><li>将证书更新为不使用 MD5 算法。 建议采用此解决方案。</li><li>如果未在源代码中动态配置绑定，将应用程序的配置文件更新为使用 TLS 1.1 或更低版本的协议。 这样便可以继续将证书和 MD5 哈希算法结合使用。</li></ul> <blockquote> [!WARNING] 不建议采用此解决方法，因为使用 MD5 哈希算法的证书被视为不安全。</blockquote> 下面的配置文件就采用了此解决方法：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;system.serviceModel&gt;&#13;&#10;&lt;bindings&gt;&#13;&#10;&lt;netTcpBinding&gt;&#13;&#10;&lt;binding&gt;&#13;&#10;&lt;security mode= &quot;None/Transport/Message/TransportWithMessageCredential&quot; &gt;&#13;&#10;&lt;transport clientCredentialType=&quot;None/Windows/Certificate&quot;&#13;&#10;protectionLevel=&quot;None/Sign/EncryptAndSign&quot;&#13;&#10;sslProtocols=&quot;Ssl3/Tls1/Tls11&quot;&gt;&#13;&#10;&lt;/transport&gt;&#13;&#10;&lt;/security&gt;&#13;&#10;&lt;/binding&gt;&#13;&#10;&lt;/netTcpBinding&gt;&#13;&#10;&lt;/bindings&gt;&#13;&#10;&lt;/system.ServiceModel&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><ul><li>如果在源代码中动态配置了绑定，将 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType> 属性更新为在源代码中使用 TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) 或更早版本的协议。</li></ul> <blockquote> [!WARNING] 不建议采用此解决方法，因为使用 MD5 哈希算法的证书被视为不安全。</blockquote> |
|范围|次要|
|版本|4.6|
|类型|运行时|

