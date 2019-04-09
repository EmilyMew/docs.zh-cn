---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760169"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>某些 .NET SDK 工具的改进的辅助功能

|   |   |
|---|---|
|详细信息|在 .NET Framework SDK 4.7.1 中，已通过修复各种辅助功能问题，改进了 SvcConfigEditor.exe 和 SvcTraceViewer.exe 工具。 其中大多数都是一些小问题，如未定义名称或未正确实现某些 UI 自动化模式。 虽然许多用户不会意识到这些小问题的重要性，但使用屏幕阅读器等辅助技术的客户会发现这些 SDK 工具更易于访问。 当然，这些修复程序改变了以前的某些行为，如键盘焦点顺序。为获取这些工具中的所有辅助功能修复程序，可对 app.config 文件执行以下操作：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|版本|4.7.1|
|类型|重定目标|

