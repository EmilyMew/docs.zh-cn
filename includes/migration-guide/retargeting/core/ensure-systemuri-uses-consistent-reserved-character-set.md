---
ms.openlocfilehash: 4f92d773197c914a74dd7e9c18f5aab5309358ae
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760789"
---
### <a name="ensure-systemuri-uses-a-consistent-reserved-character-set"></a>确保 System.Uri 使用一致的保留字符集

|   |   |
|---|---|
|详细信息|在 <xref:System.Uri?displayProperty=fullName> 中，某些有时会被解码的百分比编码字符现在始终保持编码状态。 这种情况发生在访问 URI 的路径、查询、片段或用户信息组件的属性和方法中。 仅当以下两项均为 true 时，该行为才会更改：<ul><li>URI 包含以下任意保留字符的编码形式：<code>:</code>、<code>'</code>、<code>(</code>、<code>)</code>、<code>!</code> 或 <code>*</code>。</li><li>URI 包含 Unicode 或编码的非保留字符。 如果以上两项均为 true，则编码的保留字符保持编码状态。 在先前版本的 .NET Framework 中，它们为解码状态。</li></ul>|
|建议|对于面向 .NET Framework 4.7.2 及更高版本的应用程序，默认启用新的解码行为。 如果不需要此更改，可通过将以下 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 开关添加到应用程序配置文件的 <code>&lt;runtime&gt;</code> 部分，从而禁用更改：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>对于面向 .NET Framework 早期版本，但在 .NET Framework 4.7.2 及更高版本下运行的应用程序，默认禁用新的解码行为。 可通过将以下 [AppContextSwitchOverrides](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 开关添加到应用程序配置文件的 <code>&lt;runtime&gt;</code> 部分，进行启用：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.7.2|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|

