---
ms.openlocfilehash: c8a6870a9d34889dd8f5305035744bfc63be6af6
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760715"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>存在 Unicode 时支持特殊的相对 URI 表示法

|   |   |
|---|---|
|详细信息|在包含 Unicode 的特定相对 URI 上调用 <xref:System.Uri.TryCreate%2A> 时，<xref:System.Uri> 不再引发 <xref:System.NullReferenceException>。以下是最简单的 <xref:System.NullReferenceException> 重现，两个语句等效：<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre>若要重现 <xref:System.NullReferenceException>，以下各项必须为 true：<ul><li>必须将 URI 指定为相对，方法是在其前追加“http:”，且其后不跟“//”。</li><li>URI 必须包含百分比编码的 Unicode 或未保留的符号。</li></ul>|
|建议|根据此行为禁用相对 URI 的用户应在创建 URI 时转而指定 <xref:System.UriKind.Absolute?displayProperty=nameWithType>。|
|范围|边缘|
|版本|4.7.2|
|类型|运行时|
|受影响的 API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|

