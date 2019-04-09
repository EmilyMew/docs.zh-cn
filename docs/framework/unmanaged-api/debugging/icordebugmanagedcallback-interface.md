---
title: ICorDebugManagedCallback 接口
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eacd10eecf2a8a2fc1b73a7f97eef5cb5eabafd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133713"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback 接口
提供用于处理调试器回调的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Break 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|通知调试器时<xref:System.Reflection.Emit.OpCodes.Break>执行代码流中的指令。|  
|[Breakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|遇到断点时，会通知调试器。|  
|[BreakpointSetError 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|通知调试器，公共语言运行时 (CLR) 无法准确地绑定在实时 (JIT) 编译函数之前设置的断点。|  
|[ControlCTrap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|通知调试器，正在调试的进程中捕获了 CTRL + C。|  
|[CreateAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|通知调试器已创建的应用程序域。|  
|[CreateProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|通知调试器已附加或第一次启动进程时。|  
|[CreateThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|通知调试器线程已开始执行托管的代码。|  
|[DebuggerError 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|通知调试器在尝试处理来自 CLR 的事件已发生了错误。|  
|[EditAndContinueRemap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|已否决。 通知调试器已被重新映射事件发送到 IDE。|  
|[EvalComplete 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|通知调试器已完成评估。|  
|[EvalException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|通知调试器评估已被终止与未经处理的异常。|  
|[Exception 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|通知调试器已从托管代码中引发异常。|  
|[ExitAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|通知调试器已退出应用程序域。|  
|[ExitProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|通知调试器进程已退出。|  
|[ExitThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|通知调试器执行托管的代码的线程已退出。|  
|[LoadAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|通知调试器已成功加载 CLR 程序集。|  
|[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|通知调试器已加载的类。|  
|[LoadModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|通知调试器已成功加载 CLR 模块。|  
|[LogMessage 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|通知调试器 CLR 托管线程已调用的一个方法<xref:System.Diagnostics.EventLog>类来记录事件。|  
|[LogSwitch 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|通知调试器 CLR 托管线程已调用的一个方法<xref:System.Diagnostics.Switch>类来创建、 修改或删除调试/跟踪开关。|  
|[NameChange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|通知调试器的应用程序域或线程的名称已更改。|  
|[StepComplete 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|通知调试器步骤已完成。|  
|[UnloadAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|通知调试器已卸载 CLR 程序集。|  
|[UnloadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|通知调试器卸载某个类。|  
|[UnloadModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|通知调试器已卸载 CLR 模块 (DLL)。|  
|[UpdateModuleSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|通知调试器 CLR 模块的符号已发生更改。|  
  
## <a name="remarks"></a>备注  
 所有回调都是序列化、 同一线程中调用，调用进程处于同步状态。  
  
 每个回调实现必须调用[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)继续执行。 如果`ICorDebugController::Continue`不会调用回调返回，进程将保持停止状态并没有更多事件的回调会直到之前`ICorDebugController::Continue`调用。  
  
 调试程序必须实现[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)如果它调试.NET Framework 2.0 版应用程序。 实例`ICorDebugManagedCallback`或`ICorDebugManagedCallback2`传递到回调对象作为[icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)。  
  
> [!NOTE]
>  此接口不支持跨计算机或跨进程远程调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebug 接口](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
