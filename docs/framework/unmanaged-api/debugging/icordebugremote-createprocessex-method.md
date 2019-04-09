---
title: ICorDebugRemote::CreateProcessEx 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a38812803127857281f9766fa3ed551971ec0330
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093511"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx 方法
将启动在调试器下远程计算机上的进程。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a>参数  
 `pRemoteTarget`  
 [in]指向[ICorDebugRemoteTarget 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)。 用于确定远程计算机将在其启动进程。  
  
 `lpApplicationName`  
 [in]指向一个以 null 结尾的字符串，指定要执行的启动进程的模块。 调用进程的安全上下文中执行模块。  
  
 `lpCommandLine`  
 [in]指定要执行的启动进程的命令行的以 null 结尾的字符串指针。  
  
 `lpProcessAttributes`  
 [in]未使用的远程调试。  
  
 `lpThreadAttributes`  
 [in]未使用的远程调试。  
  
 `bInheritHandles`  
 [in]未使用的远程调试。  
  
 `dwCreationFlags`  
 [in]未使用的远程调试。  
  
 `lpEnvironment`  
 [in]指向新的进程的环境块的指针。  
  
 `lpCurrentDirectory`  
 [in]指向一个以 null 结尾的字符串，指定进程的当前目录的完整路径。 如果此参数为 null，新进程将与调用进程具有相同的当前驱动器和目录。  
  
 `lpStartupInfo`  
 [in]未使用的远程调试。  
  
 `lpProcessInformation`  
 [in]未使用的远程调试。  
  
 `debuggingFlags`  
 [in]未使用的远程调试。  
  
 `ppProcess`  
 [out]指向表示进程的"ICorDebugProcess 接口"对象的地址的指针。  
  
## <a name="return-value"></a>返回值  
 S_OK  
 已成功启动远程计算机和返回"ICorDebugProcess 接口"上的进程进行调试。  
  
 E_FAIL（或其他 E_ 返回代码）  
 无法启动远程计算机上的进程并返回"ICorDebugProcess 接口"进行调试。  
  
## <a name="remarks"></a>备注  
 Silverlight 不支持混合模式调试。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl  
  
 **库：** CorGuids.lib  
  
 **.NET framework 版本：** 4.5，4，3.5 SP1  
  
## <a name="see-also"></a>请参阅

- [ICorDebugRemote 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug 接口](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
