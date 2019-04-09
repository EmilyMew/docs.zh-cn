---
title: <runtime> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3ac5fdeaebfd67d6ad4f68166fda588b9e58ca98
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119517"
---
# <a name="runtime-element"></a>\<运行时 > 元素
提供公共语言运行时用于配置应用程序的信息。  
  
 \<configuration>  
\<运行时 >  
  
## <a name="syntax"></a>语法  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 以下各节描述了子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|指定 Windows 标识始终流经异步点，而不考虑执行模拟的方式。|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|定义 <xref:System.AppContext> 类使用的一个或多个开关，用于提供新功能的选择退出机制。|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|指定为过程中的默认应用程序域提供应用程序域管理器的程序集。|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|指定用作默认应用程序域的应用程序域管理器的类型。|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|指示运行时在过程的生命周期过程中收集所有应用程序域的统计数据。|  
|[\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|包含有关程序集版本重定向和程序集位置的信息。|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|指定是否应绕过对受信任的程序集进行强名称验证。|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|指定执行字符串比较时，运行时应使用旧排序行为。|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|指定运行时是否搜索由 DEVPATH 环境变量指定的目录中的程序集。|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|指定是否禁用缓存绑定故障，即.NET Framework 2.0 版中的默认行为。|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|指定在线程启动时是否提交完整线程堆栈。|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|指定是否禁用允许运行时主机为应用程序域重写配置设置的默认行为。|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|确定日期和时间分析方法是否使用调整后的一组规则来分析仅包含天、月、小时和 AM/PM 指示符的日期字符串。|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|指定是否强制执行以下计算机配置要求：加密算法必须符合美国联邦信息处理标准 (FIPS)。|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|指定是否为公共语言运行时事件启用 Windows 事件跟踪 (ETW)。|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|指定 PerfCounter.dll 是否使用 .NET Framework 版本 1.1 应用程序中的 CategoryOptions 注册表设置，以确定是否加载来自特定于类别的共享内存或全局内存的性能计数器数据。|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|在 64 位平台上，启用总大小大于 2 千兆字节 (GB) 的数组。|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|指定公共语言运行时是否并发运行垃圾回收。|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|指定垃圾回收是否支持多个 CPU 组。|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|指定公共语言运行时是否运行服务器垃圾回收。|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|指定运行时是否使用代码访问安全性 (CAS) 发布服务器策略。|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|指定运行时是否允许托管的代码捕获访问冲突和其他损坏状态异常。|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|指定 Windows 标识不流经异步点，而不考虑当前线程上执行上下文的流设置。|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|指定是否将来自远程源的程序集加载为完全信任。|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|指定运行时是否使用旧版代码访问安全性 (CAS) 策略。|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|指定运行时是否以减慢托管和非托管代码之间的转换速度为代价，在运行时自动修复不正确的平台调用声明。|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|指定运行时是否使用固定的内存量来计算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的哈希代码。|  
|[\<PreferComInsteadOfRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|指定运行时将使用 COM 互操作来代替跨应用程序域边界的远程。|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|优化附属程序集的探测。|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|指定卷影复制是否使用 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 中引入的默认启动行为，或恢复到 .NET Framework 的早期版本的启动行为。|  
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|通过禁用将程序集视为等效于应用程序可移植性用途的默认行为来指定应用程序可以在两种不同的 .NET Framework 实现中引用同一程序集。|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|提供默认内存中对象缓存的配置信息。|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|指定运行时是否跨所有 CPU 组分发托管的线程。|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|指定未经处理的任务异常是否应终止正在运行的进程。|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|指定运行时是否使用 <xref:System.TimeSpan> 值的旧格式。|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|确定公共语言运行时是否使用实时编译的旧版 64 位 JIT 编译器。|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|指定运行时是否按应用程序域计算字符串的哈希代码。|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|请求运行时在创建内部使用的某些线程时使用显式堆栈大小，而不是默认堆栈大小。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
  
## <a name="remarks"></a>备注  
 中的子元素[\<运行时 >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)配置文件节由公共语言运行时，若要配置应用程序的执行方式。 例如， [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)元素确定垃圾回收器使用工作站垃圾回收或服务器垃圾回收[ \<Userandomizedstringhashalgorithm，那么 >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)元素可确定公共语言运行时是否计算上每个程序或每个应用程序域为基础，字符串的哈希代码和`AppContextSwitchOverrides`元素允许库用户若要选择加入或退出更改库提供的功能。  
  
 中的元素[\<运行时 >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)部分由公共语言运行时在应用程序启动时自动读取。 您还可以通过提供到其名称定义一个非默认应用程序域的配置文件<xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType>属性; 其设置将应用程序域加载时自动读取。 您应该很少，即使有的话会需要直接读取中的设置[\<运行时 >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)应用程序的配置文件中的部分。  
  
## <a name="see-also"></a>请参阅

- [运行时设置架构](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [配置文件架构](../../../../../docs/framework/configure-apps/file-schema/index.md)
