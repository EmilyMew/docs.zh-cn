---
title: ICorDebugModule3::CreateReaderForInMemorySymbols 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccfe83707b6354c42a4c3c81e911918b2ea79ec4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108909"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols 方法
创建动态模块的调试符号读取器。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>参数  
 riid  
 [in]若要返回的 COM 接口的 IID。 通常情况下，这是[ISymUnmanagedReader 接口](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)。  
  
 ppObj  
 [out]指针到指向返回的接口。  
  
## <a name="return-value"></a>返回值  
 S_OK  
 已成功创建读取器。  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 该模块不是一个内存中或动态模块。  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 符号未由应用程序提供或尚不可用。  
  
 E_FAIL（或其他 E_ 返回代码）  
 无法创建读取器。  
  
## <a name="remarks"></a>备注  
 此方法也可以是用于创建符号读取器对象的内存中 （非动态） 模块，但只有后首次了可用的符号 (由[UpdateModuleSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)回调)。  
  
 此方法返回的新实例，每次调用时 (如[CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance))。 因此，调试器应缓存的结果，并请求一个新实例，仅当基础数据可能已更改时 (即，当[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)收到回调)。  
  
 动态模块之前已加载的第一个类型不具有任何可用的符号 (如所示[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)回调)。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET framework 版本：** 4.5，4，3.5 SP1  
  
## <a name="see-also"></a>请参阅

- [ICorDebugRemoteTarget 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug 接口](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
