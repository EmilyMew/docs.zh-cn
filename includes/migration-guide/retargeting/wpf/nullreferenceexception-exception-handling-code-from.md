---
ms.openlocfilehash: bae7d11f29609acddaf9f6391983176ccaa9ebcb
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760177"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>ImageSourceConverter.ConvertFrom 异常处理代码中的 NullReferenceException

|   |   |
|---|---|
|详细信息|<xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> 的异常处理代码中的错误导致引发不正确 <xref:System.NullReferenceException?displayProperty=name> 而不是预期的异常（例如 <xref:System.IO.DirectoryNotFoundException?displayProperty=name>、<xref:System.IO.FileNotFoundException?displayProperty=name>）。 此更改更正了该错误，因此，该方法现在将引发正确的异常。 <p/>默认情况下，所有面向 .NET Framework 4.6.2 和更低版本的应用程序都将继续引发 <xref:System.NullReferenceException?displayProperty=name> 以确保兼容性。 面向 .NET Framework 4.7 和更高版本的开发人员应该能看到正确的异常。|
|建议|想要还原为在面向 .NET Framework 4.7 时获取 <xref:System.NullReferenceException?displayProperty=name> 的开发人员可以将以下内容添加/合并到应用程序的 App.config 文件：<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|范围|边缘|
|Version|4.7|
|类型|重定目标|
|受影响的 API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

