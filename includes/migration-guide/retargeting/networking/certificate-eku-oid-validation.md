---
ms.openlocfilehash: 0ddd554aa114395085a9f8ff41a99ca9a6096a51
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760984"
---
### <a name="certificate-eku-oid-validation"></a>证书 EKU OID 验证

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.6 开始，<xref:System.Net.Security.SslStream> 或 <xref:System.Net.ServicePointManager> 类执行增强型密钥使用 (EKU) 对象标识符 (OID) 验证。 增强型密钥使用 (EKU) 扩展是指示使用密钥的应用程序的对象标识符 (OID) 的集合。 EKU OID 验证使用远程证书回叫来确保远程证书具有用于预期目的的正确 OID。|
|建议|如果无需此更改，则可通过将以下切换添加到应用配置文件的 [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 中的 [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 来禁用证书 EKU OID 验证：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] 此设置仅用于后向兼容性。 否则不建议使用它。</blockquote> |
|范围|次要|
|版本|4.6|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

