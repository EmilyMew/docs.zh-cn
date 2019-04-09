---
ms.openlocfilehash: de40d16dbb5e7a7a49ae0988342b3eb75bc078c5
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760978"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>CurrentCulture 和 CurrentUICulture 在任务之间流动

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.6 开始，<xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 存储在线程的 <xref:System.Threading.ExecutionContext?displayProperty=name> 中，可跨异步操作流动。这意味着对 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 的更改将反映在稍后以异步方式运行的任务中。 这与旧版 .NET Framework 的行为不同（旧版会在所有异步任务中重置 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>）。|
|建议|受此更改影响的应用可通过将所需的 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 显式设置为异步任务中的首个操作来暂时解决此问题。 或者，可通过设置以下兼容性开关选择使用旧行为（不流动 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>）：<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>.NET Framework 4.6.2 中的 WPF 已修复此问题。 .NET Frameworks 4.6、4.6.1 中也通过 [KB 3139549](https://support.microsoft.com/kb/3139549) 修复了此问题。 面向 .NET Framework 4.6 或更高版本的应用程序将自动在 WPF 应用程序中获取正确行为 - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 将在调度程序操作中保留。|
|范围|次要|
|版本|4.6|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType></li><li><xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType></li><li><xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType></li></ul>|

