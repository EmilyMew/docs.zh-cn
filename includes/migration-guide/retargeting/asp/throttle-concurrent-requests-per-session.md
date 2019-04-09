---
ms.openlocfilehash: db8eb017bdf166b0f1a241f5a8f7db9b9430898a
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760171"
---
### <a name="throttle-concurrent-requests-per-session"></a>每个会话的限制并发请求数

|   |   |
|---|---|
|详细信息|在 .NET Framework 4.6.2 和更早版本中，ASP.NET 使用相同的 Sessionid 依次执行请求，且 ASP.NET 始终默认通过 cookie 发出 Sessionid。 如果页面响应时间较长，只需在浏览器上按 F5 即可显著降低服务器性能。 在此修复程序中，我们添加了一个计数器来跟踪排队的请求，并在请求超过指定限制时终止请求。 默认值为 50。 如果达到限制，事件日志中会记录一条警告，并且 IIS 日志中可能会记录 HTTP 500 响应。|
|建议|若要还原旧行为，可以在 web.config 文件中添加下面的设置，从而选择禁用新行为。<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|Version|4.7|
|类型|重定目标|

