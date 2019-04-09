---
ms.openlocfilehash: e80748c183a10cac4ef66c96ab48458cd9baa806
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "52742368"
---
### <a name="tabcontrol-selectionchanged-event-and-selectedcontent-property"></a>TabControl SelectionChanged 事件和 SelectedContent 属性

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.7.1 开始，当选择发生变化时，<xref:System.Windows.Controls.TabControl> 在引发 <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> 事件之前更新其 <xref:System.Windows.Controls.TabControl.SelectedContent> 属性的值。而在 .NET Framework 4.7 和更早版本中，在事件发生之后才更新到 SelectedContent。|
|建议|对于面向 .NET Framework 4.7.1 或更高版本的应用，可以在应用程序配置文件的 <code>&lt;runtime&gt;</code> 部分添加以下内容，从而选择弃用此更改并启用旧版行为：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>对于面向 .NET Framework 4.7 或更早版本，但在 .NET Framework 4.7.1 或更高版本上运行的应用，可以在应用程序配置文件的 <code>&lt;runtime&gt;</code> 部分中添加以下代码行，从而启用新的行为：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.TabControl.SelectionPropertiesCanLagBehindSelectionChangedEvent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.7.1|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Windows.Controls.TabControl.SelectedContent?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.Selector.SelectionChanged?displayProperty=nameWithType></li></ul>|

