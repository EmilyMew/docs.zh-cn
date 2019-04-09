---
ms.openlocfilehash: 12ba683655319e42368f9f2a6cf7bf70e1dbd77d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760170"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>默认的 SignedXML 和 SignedXMS 算法已更改为 SHA256

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.7 及早期版本中，SignedXML 和 SignedCMS 默认为 SHA1 以执行某些操作。从 .NET Framework 4.7.1 开始，默认情况下启用 SHA256 来执行这些操作。 此更改是必需的，因为 SHA1 不再是安全的。|
|建议|有两个新的上下文切换值，用于控制默认情况下使用 SHA1（不安全）还是 SHA256：<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>对于面向 .NET Framework 4.7.1 及更高版本的应用程序，如果不希望使用 SHA256，则可通过将以下配置开关添加到应用配置文件的[运行时](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)部分，将默认值还原为 SHA1：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>对于面向 .NET Framework 4.7 及更高版本的应用程序，可通过将以下配置开关添加到应用配置文件的[运行时](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)部分，来选择使用此更改：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.7.1|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|

