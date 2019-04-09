---
ms.openlocfilehash: 2f5511b7694f91893b731805119b85d1a5669a33
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760173"
---
### <a name="serialization-of-control-characters-with-datacontractjsonserializer-is-now-compatible-with-ecmascript-v6-and-v8"></a>使用 DataContractJsonSerializer 控制字符的序列化现在与 ECMAScript V6 和 V8 兼容

|   |   |
|---|---|
|详细信息|在 .NET framework 4.6.2 及更低版本中，<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=name> 未按与 ECMAScript V6 和 V8 标准兼容的方式对一些特殊控制字符（如 \b、\f 和 \t）进行序列化。 从 .NET Framework 4.7 开始，这些控制字符的序列化与 ECMAScript V6 和 V8 兼容。|
|建议|对面向 .NET Framework 4.7 的应用，默认启用此功能。 如果不需要此行为，可以在 app.config 或 web.config 文件的 <code>&lt;runtime&gt;</code> 部分中添加下面的代码行，从而选择禁用此功能：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Runtime.Serialization.DoNotUseECMAScriptV6EscapeControlCharacter=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|Version|4.7|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlDictionaryWriter,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject(System.Xml.XmlWriter,System.Object)?displayProperty=nameWithType></li></ul>|

