---
title: ICorDebugManagedCallback2::MDANotification 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 425c606b1f340bbd49cfe3497d394d5ad0dd37a9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133465"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification 方法
提供了执行代码遇到正在调试的应用程序中托管调试助手 (MDA) 的通知。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>参数  
 `pController`  
 [in]ICorDebugController 接口公开进程或在其中发生 MDA 的应用程序域的指针。  
  
 调试程序不应造成任何假设控制器是一个进程或应用程序域，但它始终可以查询接口来确定。  
  
 `pThread`  
 [in]指向公开托管的线程在其调试事件发生的 ICorDebugThread 接口的指针。  
  
 如果 MDA 将出现在非托管线程，值`pThread`将为 null。  
  
 你必须从 MDA 对象本身获取操作系统 (OS) 线程 ID。  
  
 `pMDA`  
 [in]一个指向[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)公开 MDA 的信息的接口。  
  
## <a name="remarks"></a>备注  
 MDA 是启发式警告，无需任何显式调试器操作调用除外[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)恢复正在调试的应用程序的执行。  
  
 公共语言运行时 (CLR) 可以确定哪些 Mda 会触发，以及哪些数据是在任意给定 MDA 在任何时间。 因此，调试器不应生成需要特定的 MDA 模式的任何功能。  
  
 可能已排队并触发遇到 MDA 后不久 Mda。 如果运行时需要等待，直到它达到中用于引发 MDA，而不是 MDA 激发，则当它遇到某一安全点，则可能发生这种情况。 这还意味着在运行时可能会激发在排队的回调 （类似于"附加"事件操作） 的一组多个 Mda。  
  
 调试程序应发布到的引用`ICorDebugMDA`后立即从返回的实例`MDANotification`回调，以允许 CLR 回收 MDA 所占用的内存。 如果多个 Mda 还将触发，释放实例可能会提高性能。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [使用托管调试助手诊断错误](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
