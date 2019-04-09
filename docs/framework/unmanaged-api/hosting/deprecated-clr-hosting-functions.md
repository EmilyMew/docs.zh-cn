---
title: 弃用的 CLR 承载函数
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa84ca0defd173563817673aad183a8b64226d41
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135795"
---
# <a name="deprecated-clr-hosting-functions"></a>弃用的 CLR 承载函数
本部分介绍早期版本的承载 API 使用的非托管全局静态函数。  
  
 除了基础结构函数 (`_Cor*`函数)，仅供.NET Framework，这些函数中已弃用[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="activation-functions"></a>激活函数  
 [ClrCreateManagedInstance 函数](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 已否决。 创建指定的托管类型的实例。  
  
 [CoInitializeCor 函数](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 已过时。 若要初始化公共语言运行时 (CLR)，使用[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。  
  
 [CoInitializeEE 函数](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 已否决。 确保 CLR 执行引擎已加载到进程。 使用[iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法相反。  
  
 [CorBindToCurrentRuntime 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 已否决。 通过使用版本信息的 XML 文件中存储公共语言运行时 (CLR) 加载到进程中。  
  
 [CorBindToRuntime 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 已否决。 使非托管的宿主能够将 CLR 加载到进程中。  
  
 [CorBindToRuntimeByCfg 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 已否决。 通过使用从 XML 文件中读取的版本信息将 CLR 加载到进程中。  
  
 [CorBindToRuntimeEx 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 已否决。 启用非托管的宿主能够将 CLR 加载到进程中，并允许您设置标志以指定 CLR 的行为。  
  
 [CorBindToRuntimeHost 函数](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 已否决。 使主机能够加载到进程的指定的版本的 CLR。  
  
 [GetCORRequiredVersion 函数](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 已否决。 获取所需的 CLR 版本号。  
  
 [GetCORSystemDirectory 函数](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 已否决。 返回加载到进程中 CLR 的安装目录。  
  
 [GetRealProcAddress 函数](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 已否决。 获取指定从最新的已安装的 CLR 版本导出的函数的地址。  
  
 [GetRequestedRuntimeInfo 函数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 已否决。 获取有关应用程序请求的 CLR 版本和目录信息。  
  
## <a name="clr-version-functions"></a>CLR 转换函数  
 在本部分中的函数返回 CLR 版本;它们不激活 CLR。  
  
 [GetCORVersion 函数](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 已否决。 返回在当前进程中运行 CLR 的版本号。  
  
 [GetFileVersion 函数](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 已否决。 获取指定的文件，使用指定的缓冲区的 CLR 版本信息。  
  
 [GetRequestedRuntimeVersion 函数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 已否决。 获取由指定的应用程序请求的 CLR 的版本号。 如果未安装该版本，获取所请求的版本之前已安装的最新版本。  
  
 [GetRequestedRuntimeVersionForCLSID 函数](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 已否决。 获取具有指定 CLSID 的类的适当 CLR 版本信息。  
  
 [GetVersionFromProcess 函数](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 已否决。 获取与指定的进程句柄关联的 CLR 的版本号。  
  
 [LockClrVersion 函数](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 已否决。 允许宿主确定在进行显式初始化 CLR 之前将在进程中使用 CLR 的版本。  
  
## <a name="hosting-functions"></a>承载函数  
 [CallFunctionShim 函数](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 已否决。 将指定的库中具有指定的名称和参数的函数调用。  
  
 [CoEEShutDownCOM 函数](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 已否决。 卸载过程中的 COM 程序集。  
  
 [CorExitProcess 函数](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 已否决。 关闭当前的非托管进程。  
  
 [CorLaunchApplication 函数](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 已否决。 启动指定的网络路径，使用指定的清单和其他应用程序数据的应用程序。  
  
 [CorMarkThreadInThreadPool 函数](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 已否决。 将标记为托管代码的执行当前正在执行的线程池线程。 从.NET Framework 2.0 版开始，此函数没有任何影响。 它不是必需的并可以从你的代码。  
  
 [CoUninitializeCor 函数](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 已过时。 CLR 不能从进程中卸载。  
  
 [CoUninitializeEE 函数](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 已过时。  
  
 [CreateDebuggingInterfaceFromVersion 函数](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 已否决。 创建[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)对象根据指定的版本信息。  
  
 [CreateICeeFileGen 函数](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 已否决。 创建[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)对象。  
  
 [DestroyICeeFileGen 函数](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 已否决。 销毁[ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md)对象。  
  
 [FExecuteInAppDomainCallback 函数指针](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 已否决。 指向 CLR 调用以执行托管的代码的函数。  
  
 [FLockClrVersionCallback 函数指针](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 已否决。 指向 CLR 调用以通知宿主的函数的初始化已开始或完成。  
  
 [GetCLRIdentityManager 函数](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 已否决。 获取一个指针指向允许 CLR 管理标识的接口。  
  
 [LoadLibraryShim 函数](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 已否决。 加载指定的版本的.NET Framework DLL。  
  
 [LoadStringRC 函数](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 已否决。 通过使用当前线程的默认区域性将 HRESULT 值转换成一条错误消息。  
  
 [LoadStringRCEx 函数](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 已否决。 将转换为相应的错误消息为指定的区域性的 HRESULT 值。  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE 函数指针](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 已否决。 指向通知主机时的重叠的函数 (即异步) 到设备的 I/O 已完成。  
  
 [LPTHREAD_START_ROUTINE 函数指针](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 已否决。 指向通知宿主某个线程已开始执行的函数。  
  
 [RunDll32ShimW 函数](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 已否决。 执行指定的命令。  
  
 [WAITORTIMERCALLBACK 函数指针](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 已否决。 指向函数通知宿主，等待句柄已收到信号或操作已超时。  
  
## <a name="infrastructure-functions"></a>基础结构函数  
 在本部分中的函数是用于仅在.NET Framework。  
  
 [_CorDllMain 函数](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 初始化 CLR，查找托管的入口点 DLL 程序集 CLR 头中，并开始执行。  
  
 [_CorExeMain 函数](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 初始化 CLR，查找托管的入口点的可执行程序集 CLR 头中，并开始执行。  
  
 [_CorExeMain2 函数](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 在指定的内存映射代码中执行的入口点。 由操作系统加载程序调用此函数。  
  
 [_CorImageUnloading 函数](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 卸载托管的模块映像时通知加载程序。  
  
 [_CorValidateImage 函数](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 验证托管的模块映像，并已加载后通知操作系统加载程序。  
  
## <a name="see-also"></a>请参阅

- [.NET Framework 4 承载全局静态函数](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
