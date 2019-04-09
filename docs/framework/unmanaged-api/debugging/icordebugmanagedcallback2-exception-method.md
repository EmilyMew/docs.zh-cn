---
title: ICorDebugManagedCallback2::Exception 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::Exception
helpviewer_keywords:
- ICorDebugManagedCallback2::Exception method [.NET Framework debugging]
- Exception method, ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: 78b0f14f-2fae-4e63-8412-4df119ee8468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8952b34781045089945e7e72e179e88300b5fdd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103342"
---
# <a name="icordebugmanagedcallback2exception-method"></a>ICorDebugManagedCallback2::Exception 方法
通知调试器的异常处理程序的搜索已启动。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Exception (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFrame       *pFrame,  
    [in] ULONG32              nOffset,  
    [in] CorDebugExceptionCallbackType dwEventType,  
    [in] DWORD                dwFlags  
);  
```  
  
## <a name="parameters"></a>参数  
 `pAppDomain`  
 [in]指向一个 ICorDebugAppDomain 对象，表示包含引发异常的线程的应用程序域的指针。  
  
 `pThread`  
 [in]指向一个 ICorDebugThread 对象，表示引发异常的线程的指针。  
  
 `pFrame`  
 [in]指向 ICorDebugFrame 对象表示框架，由`dwEventType`参数。 有关详细信息，请参阅备注部分中的表。  
  
 `nOffset`  
 [in]一个整数，由指定偏移量，`dwEventType`参数。 有关详细信息，请参阅备注部分中的表。  
  
 `dwEventType`  
 [in]CorDebugExceptionCallbackType 枚举，指定此异常回调类型的值。  
  
 `dwFlags`  
 [in]值为[CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)枚举，用于指定有关异常的其他信息  
  
## <a name="remarks"></a>备注  
 `Exception`异常处理过程在搜索阶段在不同的时间点调用回调。 即，它可以调用多个一次而展开异常。  
  
 正在处理的异常可以从所引用的 ICorDebugThread 对象检索`pThread`参数。  
  
 特定帧和偏移量由`dwEventType`参数，如下所示：  
  
|值 `dwEventType`|值 `pFrame`|值 `nOffset`|  
|----------------------------|-----------------------|------------------------|  
|DEBUG_EXCEPTION_FIRST_CHANCE|引发了异常帧。|在帧中的指令指针。|  
|DEBUG_EXCEPTION_USER_FIRST_CHANCE|引发的异常点最接近的用户代码帧。|在帧中的指令指针。|  
|DEBUG_EXCEPTION_CATCH_HANDLER_FOUND|包含 catch 处理程序的帧。|开始 catch 处理程序的 Microsoft 中间语言 (MSIL) 偏移量。|  
|DEBUG_EXCEPTION_UNHANDLED|NULL|未定义。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugManagedCallback2 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
