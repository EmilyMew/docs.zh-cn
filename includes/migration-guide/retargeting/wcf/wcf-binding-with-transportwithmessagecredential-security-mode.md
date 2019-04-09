---
ms.openlocfilehash: ce7e2db3f74ec24f47b1c224335451c997c4c349
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760970"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>与 TransportWithMessageCredential 安全模式绑定的 WCF

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.6.1 开始，可将使用 TransportWithMessageCredential 安全模式的 WCF 绑定设置为接收带有非对称安全密钥的未签名&quot;to&quot;标头的消息。默认情况下，.NET Framework 4.6.1 中将继续拒绝未签名&quot;to&quot;标头。 仅当应用程序使用 Switch.System.ServiceModel.AllowUnsignedToHeader 配置开关选择启用此新操作模式时，才会接受它们。|
|建议|由于这是一项可以选择使用的功能，因此它不应影响现有应用的行为。<br/>要控制是否使用新行为，请使用以下配置设置：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|透明|
|版本|4.6.1|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

