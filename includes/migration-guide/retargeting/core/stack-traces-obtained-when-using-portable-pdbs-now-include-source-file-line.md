---
ms.openlocfilehash: 4c9fde24a4c3260cf5b9e265dfd03080c5cd1d04
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760798"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a>使用便携式 PDB 时获取的堆栈跟踪现在包括源文件和行信息（如果请求）

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.7.2 开始，使用便携式 PDB 时获取的堆栈跟踪包括源文件和行信息（如果请求）。 在 .NET Framework 4.7.2 之前的版本中，即使已显式请求，使用便携式 PDB 时也不会提供源文件和行信息。|
|建议|对于面向 .NET Framework 4.7.2 的应用程序，如果不需要在使用便携式 PDB 时获取的源文件和行信息，可通过将以下内容添加到 <code>app.config</code> 文件的 <code>&lt;runtime&gt;</code> 部分，从而选择弃用：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>对于面向旧版 .NET Framework，但在 .NET Framework 4.7.2 或更高版本上运行的应用程序，可通过将以下内容添加到 <code>app.config</code> 文件的 <code>&lt;runtime&gt;</code> 部分，从而选择启用在使用便携式 PDB 时获取源文件和行信息：<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|版本|4.7.2|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)?displayProperty=nameWithType><li><xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)?displayProperty=nameWithType></li></ul>|

