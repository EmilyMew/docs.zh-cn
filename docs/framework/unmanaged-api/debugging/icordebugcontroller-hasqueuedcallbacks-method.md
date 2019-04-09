---
title: ICorDebugController::HasQueuedCallbacks 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce6ad24e5e670db21d3a6942ab4650a68ae44568
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102684"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks 方法
获取一个值，该值指示是否为指定的线程当前正在排队任何托管的回调。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>参数  
 `pThread`  
 [in]指向一个"ICorDebugThread"对象，表示在线程的指针。  
  
 `pbQueued`  
 [out]指向一个值，则该值`true`如果任何托管的回调当前都是对指定线程排队; 否则为`false`。  
  
 如果为指定 null`pThread`参数，`HasQueuedCallbacks`将返回`true`托管的回调如果当前排队等待任何线程。  
  
## <a name="remarks"></a>备注  
 回调将是一次，每次执行一个调度[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)调用。 如果它想要报告同时发生的多个调试事件，则调试器可以检查此标志。  
  
 调试事件排队时，它们已发生了，因此调试器必须清空的调试对象的状态以确保整个队列。 (调用`ICorDebugController::Continue`以清空队列。)例如，如果队列中包含两个线程上的调试事件*X*，调试器将暂停线程*X*后第一个调试事件，然后调用`ICorDebugController::Continue`，调试的第二个事件线程*X*将被调度，尽管线程被挂起。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅
