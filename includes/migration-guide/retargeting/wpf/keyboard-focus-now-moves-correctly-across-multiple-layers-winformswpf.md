---
ms.openlocfilehash: ae110d915241fe85453667e895ab54288302c20d
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760790"
---
### <a name="keyboard-focus-now-moves-correctly-across-multiple-layers-of-winformswpf-hosting"></a>现在，键盘焦点可在 WinForms/WPF 承载的多个层之间正确移动

|   |   |
|---|---|
|详细信息|请考虑 WPF 应用程序，其承载的 WinForms 控件会反过来承载 WPF 控件。 如果该层的第一个或最后一个控件是 WPF <code>System.Windows.Forms.Integration.ElementHost</code>，那么用户可能不能按 Tab 离开 WinForms 层。 此更改修复了这个问题，现在，用户能按 Tab 离开 WinForms layer.Automated 应用程序。这些应用程序依赖于绝不转义 WinForms 层的焦点可能不再按预期工作。|
|建议|如果开发人员想要利用此更改，但面向 .NET 4.7.2 以下的框架版本，他可将下列一组 AppContext 标记设置为 false，从而启用更改。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>WPF 应用程序必须选择启用所有早期的可访问性改进，才能使用之后的改进。 换言之，必须同时设置 <code>Switch.UseLegacyAccessibilityFeatures</code> 和 <code>Switch.UseLegacyAccessibilityFeatures.2</code> 开关。如果开发人员需要以前的功能，且面向 .NET 4.7.2 或更高版本，他可将以下 AppContext 标记设置为 false，从而禁用更改。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures.2=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|版本|4.7.2|
|类型|重定目标|

