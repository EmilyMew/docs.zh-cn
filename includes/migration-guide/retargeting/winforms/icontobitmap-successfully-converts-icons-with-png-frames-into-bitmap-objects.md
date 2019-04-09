---
ms.openlocfilehash: 9c2a8eca3f4498906cf703ff3b8ffb7336ff7a1b
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760974"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap 成功将带 PNG 帧的图标转换为位图对象

|   |   |
|---|---|
|详细信息|从面向 .NET Framework 4.6 的应用开始，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法成功将带 PNG 帧的图标转换为 Bitmap 对象。<p/>在面向 .NET Framework 4.5.2 和更早版本的应用中，如果 Icon 对象具有 PNG 帧，<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> 方法将引发 <xref:System.ArgumentOutOfRangeException> 异常。<p/>此更改会影响以下应用：重新编译为面向 .NET Framework 4.6 的应用，以及对在 Icon 对象具有 PNG 帧时引发的 <xref:System.ArgumentOutOfRangeException> 实施特殊处理的应用。 在.NET Framework 4.6 下运行时，转换成功，不再引发 <xref:System.ArgumentOutOfRangeException> ，因此不再调用异常处理程序。|
|建议|如果不需要此行为，可以在 app.config 文件的 <code>&lt;runtime&gt;</code> 部分中添加下面的元素，从而保留旧行为：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>如果 app.config 文件中已包含 <code>AppContextSwitchOverrides</code> 元素，则新值应与值特性合并，如下所示：<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.6|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|

