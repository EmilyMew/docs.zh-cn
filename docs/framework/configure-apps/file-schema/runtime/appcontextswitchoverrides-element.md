---
title: <AppContextSwitchOverrides> 元素
ms.custom: updateeachrelease
ms.date: 03/07/2019
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bc4cd94d3acd37244e1d5b882612e4b1da91b90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136456"
---
# <a name="appcontextswitchoverrides-element"></a>\<AppContextSwitchOverrides > 元素
定义 <xref:System.AppContext> 类使用的一个或多个开关，用于提供新功能的选择退出机制。  
  
 \<configuration>  
 \<运行时 >  
\<AppContextSwitchOverrides>  
  
## <a name="syntax"></a>语法  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`value`|必需的特性。<br /><br /> 定义一个或多个交换机名和属性及其关联的布尔值。|  
  
### <a name="value-attribute"></a>值属性  
  
|“值”|描述|  
|-----------|-----------------|  
|"name=value"|预定义的开关名称以及其值 (`true`或`false`)。 由分号分隔多个交换机名称/值对 （";"）。 有关支持的.NET Framework 的预定义的开关名称的列表，请参阅备注部分。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关运行时初始化选项的信息。|  
  
## <a name="remarks"></a>备注  
 从.NET Framework 4.6，开始`<AppContextSwitchOverrides>`配置文件中的元素允许调用方的 API 来确定自己的应用程序可以充分利用新功能还是保留与以前版本的库兼容性。 例如，如果 API 的行为已更改的库中，两个版本之间`<AppContextSwitchOverrides>`元素允许调用方的该 API，可以选择不上支持新功能的库版本的新行为。 在.NET Framework 中，调用 Api 的应用的`<AppContextSwitchOverrides>`元素也可以允许调用方的应用程序面向早期版本的.NET Framework，才能选择加入的新功能，如果产品包含的.NET framework 版本上运行自己的应用程序功能。  
  
 `value`属性的`<AppContextSwitchOverrides>`元素包括一个或多个以分号分隔名称/值对组成的单个字符串。  每个名称标识兼容性开关，并且及其对应的值是一个布尔值 (`true`或`false`)，该值指示此开关是否设置。 默认情况下，包含开关是`false`，并且库提供了新功能。 如果此开关设置，它们会仅提供以前的功能 (也就是说，其值是`true`)。 这使得库以同时允许依赖于以前的行为，可以选择不使用新功能的调用方提供的现有 API 的新行为。  
  
 .NET Framework 支持以下开关：  
  
|交换机名称|描述|引入了|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|控制 Windows Presentation Foundation 是否为控件布局使用旧算法。 有关详细信息，请参阅[缓解：WPF 布局](../../../migration-guide/mitigation-wpf-layout.md)。|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|控制使用包的签名部分 PackageDigitalSignatureManager 的默认算法是 SHA1 或 SHA256。<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|如果设置为`false`，允许基于 XAML 的工作流项目使用 Visual Studio 调试时启用了 FIPS。 如果没有它， <xref:System.NullReferenceException> System.Activities 程序集中的方法调用引发。|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|控制在调试器中的工作流实例的校验和是否使用 MD5 或 SHA1。 | .NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseSHA1HashForDebuggerSymbols`|控制工作流校验和哈希是否使用 SHA1 算法引入.NET Framework 4.7 中的默认值为 (`true`)，或者是否使用默认的 SHA256 算法引入.NET Framework 4.8 中的默认值为 (`false`)。<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Diagnostics.`<br/>`IgnorePortablePDBsInStackTraces`|堆栈跟踪获取使用便携式 Pdb 时可以包括源文件和行信息的控件。 `false` 若要包括源文件和行信息;否则为`true`。|.NET Framework 4.7.2|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|控件是否<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType>方法将引发异常时<xref:System.Drawing.Icon>对象具有 PNG 帧。 有关详细信息，请参阅[缓解：图标对象中的 PNG 帧](../../../migration-guide/mitigation-png-frames-in-icon-objects.md)。|.NET Framework 4.6|
|`Switch.System.Drawing.Text.`<br/>`DoNotRemoveGdiFontsResourcesFromFontCollection`|确定是否<xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType>添加到集合时正确释放对象<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>方法。 `true` 若要维护的旧行为;`false`要释放的专用字体的所有对象。 |.NET Framework 4.7.2|
|`Switch.System.Drawing.Printing.`<br>`OptimizePrintPreview`|控件是否的性能<xref:System.Windows.Forms.PrintPreviewDialog>针对网络打印机进行了优化。 有关详细信息，请参阅[PrintPreviewDialog 控件概述](../../../winforms/controls/printpreviewdialog-control-overview-windows-forms.md)。|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceJapaneseEraYearRanges`|控制是否为日语日历纪元会强制执行检查的年份范围。 `true` 若要强制实施的年份范围检查，和`false`来禁用它们 （默认行为）。 有关详细信息，请参阅[使用日历](../../../../standard/datetime/working-with-calendars.md)。|.NET Framework 4.6|
|`Switch.System.Globalization.EnforceLegacyJapaneseDateParsing`|控制是否在分析操作中的日本历时代的第一年作为识别仅"1"。 `true` 若要识别只有"1";`false`识别"1"或元年 （默认行为）。 有关详细信息，请参阅[使用日历](../../../../standard/datetime/working-with-calendars.md)。|.NET Framework 4.6| 
|`Switch.System.Globalization.FormatJapaneseFirstYearAsANumber`|控制是否日本历时代的第一年表示为"1"或元年在格式设置操作。 `true` 若要设置为"1"; 时代的第一年的格式`false`以其格式设置为元年 （默认行为）。 有关详细信息，请参阅[使用日历](../../../../standard/datetime/working-with-calendars.md)。|.NET Framework 4.6|
|`Switch.System.Globalization.NoAsyncCurrentCulture`|控制是否异步操作不流从调用线程的上下文。 有关详细信息，请参阅[CurrentCulture 和 CurrentUICulture 在任务之间流动](../../../migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks)。|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|控件是否<xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType>方法尝试仅与最后一个 DNS 条目的声明类型匹配。 有关详细信息，请参阅[缓解：X509CertificateClaimSet.FindClaims 方法](../../../migration-guide/mitigation-x509certificateclaimset-findclaims-method.md)。|.NET Framework 4.6.1|  
|`Switch.System.IdentityModel.`<br/>`EnableCachedEmptyDefaultAuthorizationContext`|控制是否允许 AuthorizationContext.Empty 返回可变的对象。|.NET Framework 4.6|  
|`Switch.System.IO.BlockLongPaths`|控件是否路径长度超过`MAX_PATH`（260 个字符） 引发<xref:System.IO.PathTooLongException>。 有关详细信息，请参阅[长路径支持](../../../migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support)。|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.`<br/>`DoNotUseNativeZipLibraryForDecompression`|控制是否将本机 OS 例程用于通过解压缩<xref:System.IO.Compression.DeflateStream>类。 `false` 若要使用本机 Api;`true`若要使用<xref:System.IO.Compression.DeflateStream>实现。|.NET Framework 4.7.2|
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|使用反斜杠 ("\\") 而不是正斜杠 （"/"） 作为路径分隔符中<xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType>属性。 有关详细信息，请参阅[缓解措施：ZipArchiveEntry.FullName 路径分隔符](../../../migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md)。|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|控制是否运行在使用创建的后台线程引发系统异常<xref:System.IO.Ports.SerialPort>流终止的进程。|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|控制是否使用旧版路径规范化和 URI 路径受<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType>和<xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType>方法。 有关详细信息，请参阅[缓解：路径规范化](../../../migration-guide/mitigation-path-normalization.md)和[缓解措施：路径冒号检查](../../../migration-guide/mitigation-path-colon-checks.md)。|.NET Framework 4.6.2|
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|控制是否相等进行比较的测试<xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType>具有一个对象的属性<xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType>第二个对象的属性。 有关详细信息，请参阅[MemberDescriptor.Equals 实现不正确](../../../migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals)。|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|禁用证书增强型密钥用法 (EKU) 对象标识符 (OID) 验证。 增强型密钥使用 (EKU) 扩展是指示使用密钥的应用程序的对象标识符 (OID) 的集合。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|通过禁用 SCH_SEND_AUX_RECORD 使用禁用 TLS1.0 浏览器利用针对 SSL/TLS （怪兽） 缓解措施。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|控件是否<xref:System.Net.ServicePointManager?displayProperty=nameWithType>和<xref:System.Net.Security.SslStream?displayProperty=nameWithType>类可以使用 SSL 3.0 协议。 有关详细信息，请参阅[缓解：TLS 协议](../../../migration-guide/mitigation-tls-protocols.md)。|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|禁用恢复为默认值为 Tls12、 Tls11、 Tls SystemDefault TLS 版本。|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|禁用 SslStream TLS 服务器端将发出警报。|.NET Framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |控件是否[DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer)序列化为基于 ECMAScript V6 和 V8 标准一些控制字符。 有关详细信息，请参阅[缓解：使用 DataContractJsonSerializer 对控制字符的序列化](../../../migration-guide/mitigation-serialization-control-characters.md)| .NET Framework 4.7 |
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseTimeZoneInfo`|控件是否<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>支持多个调整或仅一次调整时区的。 如果`true`，它使用<xref:System.TimeZoneInfo>类型序列化和反序列化日期和时间数据; 否则，它使用<xref:System.TimeZone>类型，不支持多个调整规则。|.NET Framework 4.6.2|
|`Switch.System.Runtime.Serialization.UseNewMaxArraySize`|控件是否<xref:System.Runtime.Serialization.ObjectManager?displayProperty=nameWithType>对象序列化和反序列化期间使用更大数组大小。 将此开关设置为`true`以提高性能的序列化和反序列化大型对象类型的关系图如<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>。 |.NET Framework 4.7.2|
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|控件是否<xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType>构造函数设置新的对象的<xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType>与现有的对象引用的属性。 有关详细信息，请参阅[缓解：ClaimsIdentity 构造函数](../../../migration-guide/mitigation-claimsidentity-constructor.md)。|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|控件是否尝试重用<xref:System.Security.Cryptography.AesCryptoServiceProvider>解密器会引发<xref:System.Security.Cryptography.CryptographicException>。 有关详细信息，请参阅[AesCryptoServiceProvider 解密器提供了可重用的转换](../../../migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform)。|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|控件是否的值[CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle)属性是[IntPtr](xref:System.IntPtr)表示一个窗口的内存位置处理，或者是否窗口句柄 (HWND)。 有关详细信息，请参阅[缓解：Cspparameters.parentwindowhandle 分配 HWND](../../../migration-guide/retargeting/4.6.2-4.7.md#cspparametersparentwindowhandle-now-expects-hwnd-value)。 |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|确定是否某些 SignedCMS 操作的默认值为 SHA1 或 SHA256。<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|确定是否某些 SignedXML 操作的默认值为 SHA1 或 SHA256。<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|确定是否`TransportWithMessageCredential`安全模式允许带未签名的消息"to"标头。 这是选择的开关。 有关详细信息，请参阅[.NET Framework 4.6.1 中的运行时更改](../../../migration-guide/runtime/4.5.2-4.6.1.md#windows-communication-foundation-wcf)。|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|控件是否<xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})>构造函数将引发<xref:System.ArgumentException>的元素之一是如果`null`。|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|确定是否尝试使用 X509 证书与 CSG 密钥存储提供程序引发异常。 有关详细信息，请参阅[WCF 传输安全性支持使用 CNG 存储的证书](../../../migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng)。|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableExplicitConnectionCloseHeader`|使用 HTTP 传输时与自承载服务，此值设置为`true`会导致 WCF，若要忽略应用程序添加`Connection: close`标头与请求的响应标头。 此值设置为`false`即可添加`Connection: close`到响应标头，这会导致关闭请求套接字后发送响应的标头。|.NET Framework 4.6|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|处理死锁而导致的限制为单个线程执行一次的可重入服务的实例。|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|连同`Switch.System.Net.DontEnableSchUseStrongCrypto`，确定 WCF 消息安全使用 TLS 1.1 和 TLS 1.2。|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`DontEnableSystemDefaultTlsVersions`|值为`false`设置默认配置，以允许操作系统选择协议。 值为`true`到可用的最高协议设置为默认值。 （也可在服务的以前的 framework 版本的分支）|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|确定默认消息签名的 MSMQ 消息 WCF 中的算法为 SHA1 或 SHA256。<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|控制 WCF 是否使用 SHA1 或 SHA256 哈希生成随机名称的命名管道。<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.Internals`<br/>`IncludeNullExceptionMessageInETWTrace`|控制是否引发[NullReferenceException](xref:System.NullReferenceException)异常消息为 null 时。|.NET Framework 4.7|  
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|控制是否将在服务启动时引发的异常传播到调用方的<xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>方法。|.NET Framework 4.7.1|
|`Switch.System.Uri.`<br/>`DontEnableStrictRFC3986ReservedCharacterSets`|确定是否某些有时会被解码的百分比编码字符现在始终保持编码状态。 如果`true`，它们是已解码; 否则为`false`。|.NET Framework 4.7.2|
|`Switch.System.Uri.`<br/>`DontKeepUnicodeBidiFormattingCharacters`|确定的在 Uri 中的 Unicode 双向字符的处理。 `true` 若要从 Uri; 将它们抽出`false`保留并将百分比编码它们。|.NET Framework 4.7.2|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |确定是否 Windows Presentation Foundation 应用旧算法 (`true`) 或使用新的算法 (`false`) 中分配到空间\*的列。 有关详细信息，请参阅[缓解：网格控件的空间分配到星型列](../../../migration-guide/retargeting/4.6.2-4.7.md#wpf-grid-allocation-of-space-to-star-columns)。 |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|控件是否选择器或选项卡控件始终引发所选内容之前更新其所选的值属性的值已更改事件。|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Text.`<br/>`UseAdornerForTextboxSelectionRendering`|确定是否可用于非装饰器基于所选内容呈现<xref:System.Windows.Controls.TextBox>并<xref:System.Windows.Controls.PasswordBox>控制来防止封闭的文本 (`false`)，或是否仅在装饰器层呈现文本 (`true`)。|.NET Framework 4.7.2|
|`Switch.System.Windows.Data.Binding.`<br/>`IListIndexerHidesCustomIndexer`|控制是否错误地使用自定义 IList 索引器 (`false`) 或正确 (`true`) 由<xref:System.Windows.Data.Binding?displayProperty=nameWithtype>类。|.NET Framework 4.8|
|`Switch.System.Windows.DoNotScaleForDpiChanges`|确定每个系统上是否发生 DPI 更改 (值为`false`) 或每个监视器基础 (值为`true`)。|.NET Framework 4.6.2|
|`Switch.System.Windows.`<br/>`DoNotUsePresentationDpiCapabilityTier2OrGreater`|控件是否改进中的控件的大小调整<xref:System.Windows.Interop.HwndHost?displayProperty=nameWithType>WPF 中每个监视器感知模式下的运行时已禁用 (`true`) 或启用 (`false`)。|.NET Framework 4.8|
|`Switch.System.Windows.Forms.`<br/>`DomainUpDown.UseLegacyScrolling`|确定是否需要特殊处理，开发人员<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>存在控件文本时的操作。 `true` 若要处理<xref:System.Windows.Forms.DomainUpDown.UpButton>操作;`false`有关<xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>和<xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>操作正确同步。|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|选择不使用允许自定义代码<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType>实现来安全地筛选消息，而不引发异常时<xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType>调用方法。 有关详细信息，请参阅[缓解：自定义 IMessageFilter.PreFilterMessage 实现](../../../migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md)。|.NET Framework 4.6.1|  
|`Switch.System.Windows.Forms.`<br/>`UseLegacyContextMenuStripSourceControlValue`|确定是否<xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>属性返回的源控件，当用户从嵌套打开菜单时<xref:System.Windows.Forms.ToolStripMenuItem>控件。 `true` 若要返回`null`，旧的行为;`false`要返回的源控件。|.NET Framework 4.7.2|
|`Switch.System.Windows.Forms.UseLegacyToolTipDisplay`|控制是否禁用工具提示调用支持 (`true`) 或启用 (`false`)。 启用工具提示调用支持还需要定义的旧版辅助功能`Switch.UseLegacyAccessibilityFeatures`， `Switch.UseLegacyAccessibilityFeatures.2`，并`Switch.UseLegacyAccessibilityFeatures.3`全部禁用 (设置为`false`)。|.NET Framework 4.8|
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|确定是否可选`WM_POINTER`-在 WPF 应用程序中启用基于的触控/触笔堆栈。 有关详细信息，请参阅[缓解：基于指针的触控和触笔支持](../../../migration-guide/mitigation-pointer-based-touch-and-stylus-support.md)|.NET Framework 4.7|
|`Switch.System.Windows.Markup.`<br/>`DoNotUseSha256ForMarkupCompilerChecksumAlgorithm`|确定是否使用校验和的默认哈希算法为 SHA256 (`false`) 或 SHA1 (`true`)。<br>由于与 SHA1 冲突，Microsoft 建议使用 SHA256。|.NET Framework 4.7.2|
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|控制是否旧式[NullReferenceException](xref:System.NullReferenceException)引发而不是具体指示导致异常的异常 (如[DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException)或[FileNotFoundException](xref:System.IO.FileNotFoundException)。 它旨在用于通过代码取决于处理[NullReferenceException](xref:System.NullReferenceException)。 | .NET Framework 4.7 |
|`Switch.System.Workflow.ComponentModel.`<br/>`UseLegacyHashForXomlFileChecksum`|控件是否生成工作流项目中 XOML 文件的校验和哈希使用 MD5 算法 (`true`)，或是否使用引入.NET Framework 4.8 中的默认值为 SHA256 算法。<br>由于存在冲突问题 MD5，Microsoft 建议使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForSqlTrackingCacheKey`|控制是否由 SqlTrackingService 的校验和哈希使用 MD5 算法 (`true`) 对于缓存字符串，或者是否使用引入.NET Framework 4.8 中的默认值为 SHA256 算法。<br>由于存在冲突问题 MD5，Microsoft 建议使用 SHA256。|.NET Framework 4.8|
|`Switch.System.Workflow.Runtime.`<br/>`UseLegacyHashForWorkflowDefinitionDispenserCacheKey`|控制是否由工作流运行时的校验和哈希使用 MD5 算法 (`true`) 有关缓存的工作流定义，或者是否使用引入.NET Framework 4.8 中的默认值为 SHA256 算法。<br>由于存在冲突问题 MD5，Microsoft 建议使用 SHA256。|.NET Framework 4.8|
|`Switch.UseLegacyAccessibilityFeatures`|控件可访问性功能可从.NET Framework 4.7.1 开始是启用还是禁用。 | .NET Framework 4.7.1 |
|`Switch.UseLegacyAccessibilityFeatures.2`|.NET Framework 4.7.2 中可访问性功能是否已启用的控件 (`false`) 还是禁用 (`true`)。 如果`true`，`Switch.UseLegacyAccessibilityFeatures`还必须是`true`若要启用.NET Framework 4.7.1 的辅助功能。|.NET Framework 4.7.2|
|`Switch.UseLegacyAccessibilityFeatures.3`|在.NET Framework 4.8 引入可访问性功能是否已启用的控件 (`false`) 还是禁用 (`true`)。 如果`true`，`Switch.UseLegacyAccessibilityFeatures`并`Switch.UseLegacyAccessibilityFeatures.2`也必须`true`。|.NET Framework 4.8|
|`Switch.UseLegacyToolTipDisplay`|控件的工具提示是否 displaed 当用户悬停鼠标光标在 WPF 控件 (`true`)，或它们显示在键盘焦点和通过键盘快捷键 (`false`，默认行为)。 在.NET Framework 4.8 上运行但面向旧版.NET Framework 的应用程序，同时启用键盘焦点并快捷方式键支持要求`Switch.UseLegacyAccessibilityFeatures`， `Switch.UseLegacyAccessibilityFeatures.2`，并`Switch.UseLegacyAccessibilityFeatures.3`所有将设置为`false`。|.NET Framework 4.8|
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|控制是否在复合键中的空键顺序将忽略由 XSD 架构验证。 有关详细信息，请参阅[缓解：XML 架构验证](../../../migration-guide/mitigation-xml-schema-validation.md)。|.NET Framework 4.6|  
  
> [!NOTE]
>  而不是添加`AppContextSwitchOverrides`到应用程序配置文件的元素，您还可以设置这些开关以编程方式通过调用`static`（在 C# 中) 或`Shared`（在 Visual Basic)<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>方法。  
  
 库开发人员还可以定义自定义的交换机，以允许调用方可以选择不更改其库的更高版本中引入的功能。 有关更多信息，请参见 <xref:System.AppContext> 类。  
  
## <a name="switches-in-aspnet-applications"></a>在 ASP.NET 应用程序中的交换机

可以配置 ASP.NET 应用程序通过将添加使用兼容性设置[\<添加 >](../../../configure-apps/file-schema/appsettings/add-element-for-appsettings.md)元素[ \<appSettings >](../../../configure-apps/file-schema/appsettings/index.md) web.config 文件部分。 

下面的示例使用`<add>`元素添加到两个设置`<appSettings>`web.config 文件的部分：

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="example"></a>示例

 下面的示例使用`AppContextSwitchOverrides`元素来定义单个应用程序兼容性开关， `Switch.System.Globalization.NoAsyncCurrentCulture`，防止在异步方法调用中的线程间流动区域性。  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 下面的示例使用`AppContextSwitchOverrides`元素来定义两个应用程序兼容性开关`Switch.System.Globalization.NoAsyncCurrentCulture`和`Switch.System.IO.BlockLongPaths`。 请注意，用分号分隔的两个名称/值对。  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.AppContext?displayProperty=nameWithType>
- [\<运行时 > 元素](runtime-element.md)
- [\<配置 > 元素](../configuration-element.md)
