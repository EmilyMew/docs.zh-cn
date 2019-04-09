---
title: CorBindToRuntimeEx 函数
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ed383f616770fa8bab8e7a8944fa0f922017d87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122949"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx 函数
使非托管的宿主能够将公共语言运行时 (CLR) 加载到进程中。 [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)并`CorBindToRuntimeEx`函数执行相同的操作，但`CorBindToRuntimeEx`函数允许您设置标志以指定 CLR 的行为。  
  
 此函数中不推荐[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
 此函数采用一组参数的允许主机以执行以下操作：  
  
-   指定要加载的运行时版本。  
  
-   指示是否应加载服务器或工作站生成。  
  
-   控制并发垃圾回收或非并发垃圾回收是否已完成。  
  
> [!NOTE]
>  在应用程序运行在 WOW64 中不支持并发垃圾回收 x86 仿真程序上实现 Intel Itanium 体系结构 （以前称为 IA-64） 的 64 位系统。 有关在 64 位 Windows 系统上使用 WOW64 的详细信息，请参阅[运行 32 位应用程序](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
-   控制是否为非特定于域的加载程序集。  
  
-   获取到的接口指针[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)可用来设置配置的 CLR 实例之前启动的其他选项。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>参数  
 `pwszVersion`  
 [in]想要加载的 CLR 版本描述的字符串。  
  
 .NET Framework 中的版本号用句点分隔的四个部分组成： *major.minor.build.revision*。 将字符串作为传递`pwszVersion`必须以字符"v"跟版本号 (例如，"v1.0.1529") 的前三个部分开头。  
  
 某些版本的 CLR 随指定与以前版本的 CLR 的兼容性的策略语句。 默认情况下，启动填充程序的计算结果`pwszVersion`针对策略语句和加载运行时的最新版本的是与所请求的版本兼容。 主机可以强制填充程序跳过策略评估和负载中指定的确切版本`pwszVersion`通过将的值传递`STARTUP_LOADER_SAFEMODE`为`startupFlags`参数，如下所述。  
  
 如果调用方指定为 null `pwszVersion`，`CorBindToRuntimeEx`标识已安装的运行时其版本号低于.NET Framework 4 运行时，并从该组中加载运行时的最新版本的组。 如果不安装任何早期版本，它不会加载.NET Framework 4 或更高版本，并且失败。 请注意，传递 null，则主机加载的运行时版本的任何控制。 虽然这种方法可能在某些情况下适用，但强烈建议主机提供一个要加载特定版本。  
  
 `pwszBuildFlavor`  
 [in]一个字符串，指定是否加载在服务器或工作站的 clr 版本。 有效值为 `svr` 和 `wks`。 服务器生成经过优化，可充分利用多个处理器，用于垃圾回收和工作站生成优化的单处理器计算机上运行的客户端应用程序。  
  
 如果`pwszBuildFlavor`设置为 null，则将加载工作站版本。 在单处理器计算机上运行时，工作站生成始终处于加载状态，即使`pwszBuildFlavor`设置为`svr`。 但是，如果`pwszBuildFlavor`设置为`svr`，并且指定并发垃圾回收 (请参阅的说明`startupFlags`参数)，将加载服务器版本。  
  
 `startupFlags`  
 [in]值的组合[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚举。 这些标志控制并发垃圾回收、 非特定于域的代码和行为的`pwszVersion`参数。 如果未设置标志，则默认值为单一域。 以下为有效值：  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 有关这些标志的说明，请参阅[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚举。  
  
 `rclsid`  
 [in]`CLSID`的实现的组件类[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)接口。 支持的值为 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 [in]`IID`从所请求的接口的`rclsid`。 支持的值为 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 [out]指向返回的接口指针`riid`。  
  
## <a name="remarks"></a>备注  
 如果`pwszVersion`指定不存在，运行时版本`CorBindToRuntimeEx`返回 CLR_E_SHIM_RUNTIMELOAD 的 HRESULT 值。  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>执行上下文和流的 Windows 标识  
 在 CLR 版本 1<xref:System.Security.Principal.WindowsIdentity>对象不流经异步点，如新的线程，线程池或计时器回调。 在 2.0 版中的 clr<xref:System.Threading.ExecutionContext>对象封装有关当前正在执行的线程的一些信息，然后在任何异步点，但不是会跨应用程序域边界。 同样，<xref:System.Security.Principal.WindowsIdentity>对象还上任何异步点流动。 因此，在线程上的当前模拟如果有的话，也会流动。  
  
 您可以更改以下两种方式流：  
  
1.  通过修改<xref:System.Threading.ExecutionContext>设置，以禁止显示上每个线程进行的流 (请参阅<xref:System.Threading.ExecutionContext.SuppressFlow%2A>， <xref:System.Security.SecurityContext.SuppressFlow%2A>，和<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>方法)。  
  
2.  通过更改进程的默认模式为第 1 版兼容性模式，其中<xref:System.Security.Principal.WindowsIdentity>对象不流经异步的任何时刻，而不考虑<xref:System.Threading.ExecutionContext>当前线程上的设置。 如何更改默认模式取决于是否使用托管可执行文件或使用非托管承载接口能够将 CLR 加载：  
  
    1.  用于托管可执行文件，必须设置`enabled`的属性[ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)元素`true`。  
  
    2.  对于非托管承载接口，将`STARTUP_LEGACY_IMPERSONATION`中的标志`startupFlags`参数调用时`CorBindToRuntimeEx`函数。  
  
     第 1 版兼容性模式适用于整个过程和进程中的所有应用程序域。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [CorBindToCurrentRuntime 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost 接口](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [弃用的 CLR 承载函数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
