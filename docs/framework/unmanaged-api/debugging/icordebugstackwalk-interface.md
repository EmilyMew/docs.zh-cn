---
title: ICorDebugStackWalk 接口
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e33e9be112a6a10f89b88005496ce2e63dff2d54
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080678"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk 接口
提供用于获取线程堆栈上的托管方法或帧的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|返回的上下文中的当前帧`ICorDebugStackWalk`对象。|  
|[SetContext 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|集`ICorDebugStackWalk`到有效的线程的上下文对象的当前上下文。|  
|[Next 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|将移动`ICorDebugStackWalk`到下一个帧的对象。|  
|[GetFrame 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|获取当前帧中`ICorDebugStackWalk`对象。|  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
>  此接口不支持跨计算机或跨进程远程调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [调试](../../../../docs/framework/unmanaged-api/debugging/index.md)
