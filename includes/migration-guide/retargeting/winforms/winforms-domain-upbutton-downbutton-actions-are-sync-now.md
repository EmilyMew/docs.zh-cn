---
ms.openlocfilehash: 7344fddbc61d47d4ca735808f0b92f63e33e15a3
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760770"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>WinForm 的域 upbutton 和 downbutton 操作现已同步

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.7.1 和早期版本中，显示控件文本时会忽视 <xref:System.Windows.Forms.DomainUpDown> 控件的 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作，并且要求开发人员先使用控件上的 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 操作，再使用 <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 操作。 从 .NET Framework 4.7.2 开始，<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> 和 <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> 操作将在此场景中独立工作，并保持同步。|
|建议|为使应用程序从这些更改获益，它必须在 .NET Framework 4.7.2 或更高版本上运行。 此应用程序可通过以下任何一种方式从这些更改中获益：<ul><li>重新编译为面向 .NET Framework 4.7.2。 对于面向 .NET Framework 4.7.2 或更高版本的 Windows 窗体应用程序，此更改将默认启用。</li><li>通过向应用配置文件的 <code>&lt;runtime&gt;</code> 部分添加以下 [AppContext 开关](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)并将其设置为 <code>false</code>，可选择弃用旧版滚动行为，如下例所示。</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|版本|4.7.2|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType></li><li><xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType></li></ul>|

