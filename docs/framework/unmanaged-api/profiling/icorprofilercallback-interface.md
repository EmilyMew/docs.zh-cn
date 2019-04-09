---
title: ICorProfilerCallback 接口
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback
helpviewer_keywords:
- ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2f474317493b3aac421ca1270ff461b97cfe027
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125932"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback 接口
提供了公共语言运行时 (CLR) 用于探查器已订阅的事件发生时通知代码探查器的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AppDomainCreationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|通知探查器已创建的应用程序域。|  
|[AppDomainCreationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|通知探查器正在创建应用程序域。|  
|[AppDomainShutdownFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|通知探查器已从进程中卸载应用程序域。|  
|[AppDomainShutdownStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|通知探查器正在从进程卸载程序的应用程序域。|  
|[AssemblyLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|通知探查器程序集已完成加载。|  
|[AssemblyLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|通知探查器正在加载程序集。|  
|[AssemblyUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|通知探查器程序集已被卸载。|  
|[AssemblyUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|通知探查器正在卸载程序集。|  
|[ClassLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|通知探查器加载已完成某个类。|  
|[ClassLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|通知探查器正在加载的类。|  
|[ClassUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|通知探查器类已完成卸载。|  
|[ClassUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|通知探查器卸载某个类。|  
|[COMClassicVTableCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|通知探查器已创建了指定的 IID 和类的运行时可调用包装 (RCW)。|  
|[COMClassicVTableDestroyed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|通知探查器正在销毁 RCW。|  
|[ExceptionCatcherEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|通知探查器将控制权传递到相应`catch`块。|  
|[ExceptionCatcherLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|通知探查器将控制权传递带相应`catch`块。|  
|[ExceptionCLRCatcherExecute 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|在.NET Framework 2.0 版中已过时。|  
|[ExceptionCLRCatcherFound 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|在.NET Framework 2.0 中已过时。|  
|[ExceptionOSHandlerEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|未实现。 需要非托管的异常信息的探查器必须获取此信息通过其他方式。|  
|[ExceptionOSHandlerLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|未实现。 需要非托管的异常信息的探查器必须获取此信息通过其他方式。|  
|[ExceptionSearchCatcherFound 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|通知探查器的异常处理的搜索阶段已找到的处理程序引发的异常。|  
|[ExceptionSearchFilterEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|通知探查器正在执行用户筛选器。|  
|[ExceptionSearchFilterLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|通知探查器的用户筛选器只需执行完毕。|  
|[ExceptionSearchFunctionEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|通知探查器的异常处理的搜索阶段已进入一个函数。|  
|[ExceptionSearchFunctionLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|通知探查器的异常处理的搜索阶段已完成搜索函数。|  
|[ExceptionThrown 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|通知探查器已引发异常。|  
|[ExceptionUnwindFinallyEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|通知探查器处理的异常展开阶段进入`finally`子句包含在指定的函数。|  
|[ExceptionUnwindFinallyLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|通知探查器的异常展开阶段处理已离开`finally`子句。|  
|[ExceptionUnwindFunctionEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|通知探查器的异常处理展开阶段已进入一个函数。|  
|[ExceptionUnwindFunctionLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|通知探查器的异常处理展开阶段已完成展开函数。|  
|[FunctionUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|通知探查器运行时已开始卸载某个函数。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|调用以初始化探查器每次启动新的 CLR 应用程序时。|  
|[JITCachedFunctionSearchFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|通知探查器搜索已完成以前使用 NGen.exe 编译的函数。|  
|[JITCachedFunctionSearchStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|通知探查器在编译时以前使用 NGen.exe 的函数已开始搜索。|  
|[JITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|通知探查器 JIT 编译器已完成编译函数。|  
|[JITCompilationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|通知探查器在实时 (JIT) 编译器已开始编译函数。|  
|[JITFunctionPitched 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|通知探查器已从内存中删除已进行 JIT 编译的函数。|  
|[JITInlining 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|通知探查器 JIT 编译器将要插入一个嵌入另一个函数。|  
|[ManagedToUnmanagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|通知探查器已发生从托管代码到非托管代码的转换。|  
|[ModuleAttachedToAssembly 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|通知探查器模块，已附加到其父程序集。|  
|[ModuleLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|通知探查器模块已完成加载。|  
|[ModuleLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|通知探查器正在加载的模块。|  
|[ModuleUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|通知探查器模块已完成卸载。|  
|[ModuleUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|通知探查器正在卸载模块。|  
|[MovedReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|通知垃圾回收期间移动的对象引用有关探查器。|  
|[ObjectAllocated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|通知探查器内存中堆分配的对象。|  
|[ObjectReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|通知有关的对象的引用指定对象的内存探查器。|  
|[ObjectsAllocatedByClass 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|通知事件探查器关于自上次垃圾回收以来已创建的每个指定的类的实例数。|  
|[RemotingClientInvocationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|通知探查器的远程处理调用已在客户端上完成运行。|  
|[RemotingClientInvocationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|通知探查器已启动的远程处理调用。|  
|[RemotingClientReceivingReply 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|通知探查器的远程处理调用的服务器端部分已完成，而客户端正在接收并即将处理回复。|  
|[RemotingClientSendingMessage 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|通知探查器客户端向服务器发送请求。|  
|[RemotingServerInvocationReturned 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|通知探查器进程已完成调用远程方法调用请求响应中的方法。|  
|[RemotingServerInvocationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|通知探查器进程正在调用远程方法调用请求响应中的方法。|  
|[RemotingServerReceivingMessage 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|通知探查器进程正在接收远程方法调用或激活请求。|  
|[RemotingServerSendingReply 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|通知探查器进程已完成处理远程方法调用请求，并将要通过通道答复传输。|  
|[RootReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|通知探查器与垃圾回收后根引用的信息。|  
|[RuntimeResumeFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|通知探查器运行时已恢复运行时的所有线程，并已返回到正常操作。|  
|[RuntimeResumeStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|通知探查器运行时继续运行时的所有线程。|  
|[RuntimeSuspendAborted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|通知探查器运行时已中止已发生的运行时挂起。|  
|[RuntimeSuspendFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|通知探查器运行时已完成的运行时的所有线程挂起。|  
|[RuntimeSuspendStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|通知探查器运行时即将挂起运行时的所有线程。|  
|[RuntimeThreadResumed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|通知探查器正在挂起之后已恢复指定的线程。|  
|[RuntimeThreadSuspended 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|指定的线程，或者将要被，挂起通知探查器。|  
|[Shutdown 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|通知探查器正在关闭应用程序。|  
|[ThreadAssignedToOSThread 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|通知探查器正在使用特定操作系统 (OS) 线程实现一个托管的线程。|  
|[ThreadCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|通知探查器已创建一个线程。|  
|[ThreadDestroyed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|通知探查器线程已销毁。|  
|[UnmanagedToManagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|通知探查器已发生从非托管代码到托管代码的转换。|  
  
## <a name="remarks"></a>备注  
 CLR 调用中的方法`ICorProfilerCallback`(或[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) 接口以通知探查器在某一事件，探查器订阅，会发生。 这是通过其 CLR 代码探查器与进行通信的主回调接口。  
  
 代码探查器必须实现的方法`ICorProfilerCallback`接口。 为.NET Framework 2.0 或更高版本中，探查器还必须实现`ICorProfilerCallback2`方法。 每个方法的实现必须返回失败 HRESULT，它的值为成功，则为 S_OK 和 e_fail 两者之一。 目前，CLR 将忽略除每个回调返回的 HRESULT [icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)。  
  
 在 Microsoft Windows 注册表中，代码探查器必须注册实现其组件对象模型 (COM) 对象`ICorProfilerCallback`和`ICorProfilerCallback2`接口。 代码探查器订阅它需要通过调用接收通知的事件[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)。 这通常是在探查器的实现中的[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)。 然后，探查器是能够从运行时接收通知事件即将发生或正在执行的运行时进程中只发生时。  
  
> [!NOTE]
>  探查器注册的单个 COM 对象。 如果探查器面向.NET Framework 版本 1.0 或 1.1，COM 对象需要实现的方法`ICorProfilerCallback`。 如果它面向.NET Framework 2.0 或更高版本，COM 对象还必须实现的方法`ICorProfilerCallback2`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [分析接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
