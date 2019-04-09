---
title: ICorDebugStackWalk::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724db50285532c20132fbfd5262df26227db6742
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130021"
---
# <a name="icordebugstackwalknext-method"></a>ICorDebugStackWalk::Next 方法
将移动[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)到下一个帧的对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a>返回值  
 此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|在运行时成功展开至下一帧 （请参阅备注）。|  
|E_FAIL|`ICorDebugStackWalk`不为高级对象。|  
|CORDBG_S_AT_END_OF_STACK|由于此展开已达到堆栈的末尾。|  
|CORDBG_E_PAST_END_OF_STACK|帧指针已末尾的堆栈;因此，可以不访问任何其他帧。|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>备注  
 `Next`方法的改进`ICorDebugStackWalk`仅当运行时可展开当前帧对象传递给调用的帧。 否则，对象前移至下一个运行时能够展开的帧。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugStackWalk 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [调试](../../../../docs/framework/unmanaged-api/debugging/index.md)
