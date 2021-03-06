---
ms.openlocfilehash: cce19d6c9afa5f5ce9bb17b5b5d92f2060a08414
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760982"
---
### <a name="currentculture-is-not-preserved-across-wpf-dispatcher-operations"></a>在 WPF 调度程序操作上不保留 CurrentCulture

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.6 开始，在 <xref:System.Windows.Threading.Dispatcher?displayProperty=name> 中对 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 的更改将会在该调度程序操作结束时丢失。 同样，在调度程序操作外对 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 的更改在执行该操作时可能不会反映出来。实际上，这意味着 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 更改可能不会在 WPF UI 回调和 WPF 应用程序中的其他代码之间流动。这是因为，从面向 .NET Framework 4.6 的应用开始，<xref:System.Threading.ExecutionContext?displayProperty=name> 中的一项更改使 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 存储在执行上下文中。 WPF 调度程序操作存储用于启动操作的执行上下文，并在操作完成时还原以前的上下文。 由于 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 现在属于该上下文，因此，在调度程序操作中对它们所做的更改在操作之外不会保留。|
|建议|受此更改影响的应用可在字段中存储所需的 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 或 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>，并在所有调度程序操作正文（包括 UI 事件回调处理程序）中检查是否设置了正确的 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name> 和 <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name>。 或者，因为在此 WPF 更改之下的 ExecutionContext 更改仅影响面向 .NET Framework 4.6 或更高版本的应用，面向 .NET Framework 4.5.2 可避免出现此中断。面向 .NET Framework 4.6 或更高版本的应用也可以通过设置以下兼容性开关解决此问题：<pre><code class="lang-csharp">AppContext.SetSwitch(&quot;Switch.System.Globalization.NoAsyncCurrentCulture&quot;, true);&#13;&#10;</code></pre>.NET Framework 4.6.2 中的 WPF 已修复此问题。 .NET Frameworks 4.6、4.6.1 中也通过 [KB 3139549](https://support.microsoft.com/kb/3139549) 修复了此问题。 面向 .NET Framework 4.6 或更高版本的应用程序将自动在 WPF 应用程序中获取正确行为 - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=name>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=name> 将在调度程序操作中保留。|
|范围|次要|
|版本|4.6|
|类型|重定目标|

