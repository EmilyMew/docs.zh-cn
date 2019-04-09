---
title: CorDebugUserState 枚举
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54b2af6e7a200db89bfd7335868a629d7a886fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141305"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState 枚举
指示线程的用户状态。  
  
## <a name="syntax"></a>语法  
  
```  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>成员  
  
|“值”|描述|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|已请求的线程终止。|  
|`USER_SUSPEND_REQUESTED`|已请求挂起线程。|  
|`USER_BACKGROUND`|线程已在后台运行。|  
|`USER_UNSTARTED`|该线程尚未开始执行。|  
|`USER_STOPPED`|线程已终止。|  
|`USER_WAIT_SLEEP_JOIN`|线程正在等待另一个线程来完成任务。|  
|`USER_SUSPENDED`|线程已挂起。|  
|`USER_UNSAFE_POINT`|该线程是在不安全的点。 也就是说，线程处于中执行的点，它可能会阻止垃圾回收。<br /><br /> 调试事件的调度可能不安全的点，但挂起线程，在不安全的点将很有可能导致死锁在恢复该线程之前。 由实时 (JIT) 和垃圾回收实现确定的安全和不安全点。|  
|`USER_THREADPOOL`|该线程是从线程池。|  
  
## <a name="remarks"></a>备注  
 用户状态是线程的调试器检查时该线程具有的状态。 一个线程可能具有的用户状态的组合。  
  
 使用[icordebugthread:: Getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)方法来检索线程的用户状态。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试枚举](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
