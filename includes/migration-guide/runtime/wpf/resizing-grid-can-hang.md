---
ms.openlocfilehash: 2e870b8d7b8ed986863632f947223946a6604f89
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761442"
---
### <a name="resizing-a-grid-can-hang"></a>调整网格可能会挂起

|   |   |
|---|---|
|详细信息|出现以下情况时，在 <code>T:System.Windows.Controls.Grid</code> 布局期间可能会发生无限循环：<ul><li>行定义包含两个 *-行，各声明一个 MinHeight 和一个 MaxHeight。</li><li>*-行的内容不超过相应的 MaxHeight</li><li>第一个 MinHeight（加上其他任何固定行或自动行）超过了网格的可用高度</li><li>此应用面向 .NET Framework 4.7，或通过设置 <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> 选择启用 4.7 分配算法</li></ul>在超过两行时或在列出现类似情况时，也可能发生该循环。此问题已在 .NET Framework 4.7.1 中解决。|
|建议|升级到 .NET Framework 4.7.1。  或者，如果不需要 4.7 分配算法，也可以使用以下配置设置：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|Version|4.7|
|类型|运行时|

