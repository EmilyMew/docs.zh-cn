---
ms.openlocfilehash: c923d9b341bbf0a21d73ac75cc6cb1a037f37826
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760769"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>PrivateFontCollection.AddFontFile 方法释放字体资源

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.7.1 和早期版本中，为使用 <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)> 方法添加到此集合的 <xref:System.Drawing.Font> 对象设置 <xref:System.Drawing.Text.PrivateFontCollection> 后，<xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> 类不会释放 GDI+ 字体资源。 在 .NET Framework 4.7.2 和更高版本中，<xref:System.Drawing.Text.FontCollection.Dispose%2A> 会释放作为文件添加到此集合的 GDI+ 字体。|
|建议|<strong>如何选择启用或选择弃用这些更改</strong> 为使应用程序从这些更改获益，它必须在 .NET Framework 4.7.2 或更高版本上运行。 此应用程序可通过以下任何一种方式从这些更改中获益：<ul><li>重新编译为面向 .NET Framework 4.7.2。 对于面向 .NET Framework 4.7.2 或更高版本的 Windows 窗体应用程序，此更改将默认启用。</li><li>它面向 .NET Framework 4.7.1 或更早版本，通过向 app.config 文件的 <code>&lt;runtime&gt;</code> 部分添加以下 [AppContext 开关](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)并将其设置为 <code>false</code>，可选择弃用旧版辅助功能行为，如下例所示。</li></ul><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>面向 .NET Framework 4.7.2 或更高版本并希望保留旧版行为的应用程序，可通过将此 AppContext 开关显式设置为 <code>true</code> 来选择不释放字体资源。|
|范围|边缘|
|版本|4.7.2|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType></li><li><xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType></li></ul>|

