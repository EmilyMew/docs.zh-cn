---
ms.openlocfilehash: 4daa08ce4bbcfe5a7242f19506811e422d0477b7
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760724"
---
### <a name="dataannotationsdatatypeattributedisableregex-app-setting-is-on-by-default-in-net-framework-472"></a>.NET Framework 4.7.2 中默认启用 "dataAnnotations:dataTypeAttribute:disableRegEx" 应用设置

|   |   |
|---|---|
|详细信息|.NET Framework 4.6.1 中引入了应用设置 (<code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code>)，允许用户在数据类型属性（如 <xref:System.ComponentModel.DataAnnotations.EmailAddressAttribute?displayProperty=nameWithType>、<xref:System.ComponentModel.DataAnnotations.UrlAttribute?displayProperty=nameWithType> 和 <xref:System.ComponentModel.DataAnnotations.PhoneAttribute?displayProperty=nameWithType>）中禁用正则表达式。 这有助于减少安全漏洞，如可避免使用特定正则表达式进行拒绝服务攻击的可能性。<br/>在 .NET Framework 4.6.1 中，禁用 RegEx 使用这项应用设置默认设置为 <code>false</code>。 从 .NET Framework 4.7.2 开始，默认情况下，此配置开关设置为 <code>true</code>，进一步减少面向 .NET Framework 4.7.2 及更高版本的 Web 应用程序的安全漏洞。|
|建议|如果发现升级到 .NET Framework 4.7.2 后 Web 应用程序中的正则表达式不起作用，则可将 <code>&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot;</code> 设置的值更新为 <code>false</code>，从而还原到之前的行为。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appsettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;dataAnnotations:dataTypeAttribute:disableRegEx&quot; value=&quot;false&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appsettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.7.2|
|类型|运行时|

