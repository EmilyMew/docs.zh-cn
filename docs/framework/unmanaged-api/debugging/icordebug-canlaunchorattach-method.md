---
title: ICorDebug::CanLaunchOrAttach 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cf0065f1ed12ad3a37819b0a15d734a2b51ff5b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125601"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach 方法
返回一个 HRESULT，指示是否可以在当前的计算机和运行时配置的上下文中启动一个新的进程或附加到指定的现有进程。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>参数  
 `dwProcessId`  
 [in]现有的进程的 ID。  
  
 `win32DebuggingEnabled`  
 [in]传入`true`如果打算使用 Win32 调试启用，启动或 Win32 调试已启用; 否则为附加传递`false`。  
  
## <a name="return-value"></a>返回值  
 如果调试服务确定启动新进程或附加到给定的进程，则返回 S_OK 提供有关当前的计算机和运行时配置的信息。 可能的 HRESULT 值为：  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>备注  
 此方法是仅用于提供信息。 接口不会妨碍您启动或附加到进程，而不考虑值返回`CanLaunchOrAttach`。  
  
 如果你打算使用 Win32 调试启用了启动或启用 Win32 调试附加，则传递`true`为`win32DebuggingEnabled`。 通过返回的 HRESULT`CanLaunchOrAttach`如果使用此选项可能不同。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebug 接口](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
