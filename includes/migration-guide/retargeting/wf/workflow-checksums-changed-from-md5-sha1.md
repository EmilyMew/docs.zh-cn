---
ms.openlocfilehash: f007a2b81820a1d25a2d101b35f3a49e7794fec1
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760175"
---
### <a name="workflow-checksums-changed-from-md5-to-sha1"></a>工作流校验和已从 MD5 更改为 SHA1

|   |   |
|---|---|
|详细信息|为支持使用 Visual Studio 进行调试，工作流运行时使用哈希算法为工作流实例生成校验和。 在 .NET Framework 4.6.2 和早期版本中，工作流校验和哈希使用 MD5 算法，这会在启用 FIPS 的系统上导致问题。 从 .NET Framework 4.7 开始，算法为 SHA1。 如果代码保留了这些校验和，它们将是不兼容的。|
|建议|如果代码由于校验和失败而无法加载工作流实例，请尝试将 <code>AppContext</code> 开关 &quot;Switch.System.Activities.UseMD5ForWFDebugger&quot; 设置为 true。在代码中：<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Activities.UseMD5ForWFDebugger&quot;, true);&#13;&#10;</code></pre>或在配置中：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Activities.UseMD5ForWFDebugger=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.7|
|类型|重定目标|

