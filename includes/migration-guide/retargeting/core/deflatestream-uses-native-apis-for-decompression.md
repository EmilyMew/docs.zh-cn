---
ms.openlocfilehash: ed0dde302e30ae0cf3c7a8d0985f2314d91cab66
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760793"
---
### <a name="deflatestream-uses-native-apis-for-decompression"></a>DeflateStream 使用本机 API 进行解压缩

|   |   |
|---|---|
|详细信息|从 .NET Framework 4.7.2 开始，<code>T:System.IO.Compression.DeflateStream</code> 类中解压缩的实现已更改为默认使用本机 Windows API。 通常情况下，这能大大地提高性能。 所有面向 .NET Framework 4.7.2 或更高版本的 .NET 应用程序均使用本机实现。此更改可能会导致某些行为差异，其中包括：<ul><li>异常消息可能有所不同。 但是，引发的异常类型保持不变。</li><li>可能以不同的方式处理某些特殊情况（例如没有足够的内存完成操作）。</li><li>分析 gzip 标头存在一些已知差异（注意：仅影响用于解压缩的 <code>GZipStream</code> 集）：</li><li>分析无效标头时出现异常可能在不同的时间引发。</li><li>本机实现强制根据规范设置 gzip 标头（即 [FLG](http://www.zlib.org/rfc-gzip.html#header-trailer)）内的一些保留标记值，这可能导致其在忽略先前无效值的情况下引发异常。</li></ul>|
|建议|如果借助本机 API 解压缩对应用行为产生负面影响，则可通过将 <code>Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression</code> 开关添加到 app.config 文件的 <code>runtime</code> 部分并将其设置为 <code>true</code>，选择弃用此功能：<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot; ?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|范围|次要|
|版本|4.7.2|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.IO.Compression.DeflateStream?displayProperty=nameWithType></li><li><xref:System.IO.Compression.GZipStream?displayProperty=nameWithType></li></ul>|

