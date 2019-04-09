---
ms.openlocfilehash: 63a38f33fef09577c5ed621727b8c38e4c7e1bdf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760802"
---
### <a name="the-default-hash-algorithm-for-wpfs-markup-compiler-is-now-sha256"></a>现在 WPF 标记编译器的默认哈希算法为 SHA256

|   |   |
|---|---|
|详细信息|WPF 标记编译器为 XAML 标记文件提供编译服务。  在 .NET Framework 4.7.1 及更早版本中，用于校验和的默认哈希算法为 SHA1。 由于 SHA1 最近出现安全问题，从 .NET Framework 4.7.2 起，此默认算法已更改为 SHA256。  此更改会影响编译期间标记文件的所有校验和生成。|
|建议|如果开发人员面向 .NET Framework 4.7.2 或更高版本且想要还原到 SHA1 哈希行为，则必须设置以下 AppContext 标记。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>如果开发人员面向 .NET 4.7.2 更低版本且想要利用 SHA256 哈希，则必须设置以下 AppContext 标记。  请注意，安装的 .NET Framework 必须是 4.7.2 或更高版本。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Markup.DoNotUseSha256ForMarkupCompilerChecksumAlgorithm=false&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|范围|透明|
|版本|4.7.2|
|类型|重定目标|

