---
title: ICorDebugCode3::GetReturnValueLiveOffset 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03ee275336d3ae71f63d82add694fe1308efbe8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125926"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset 方法
对于指定的 IL 偏移量，获取本机偏移量，以便调试器可以从函数获取返回值应放置一个断点。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a>参数  
 `ILoffset`  
 IL 偏移量。 它必须是函数调用站点，否则函数调用将失败。  
  
 `bufferSize`  
 可用来存储的字节数`pOffsets`。  
  
 `pFetched`  
 指向实际返回的偏移量数的指针。 通常情况下，其值为 1，但单个 IL 指令可以映射到多个`CALL`程序集指令。  
  
 `pOffsets`  
 本机偏移量的数组。 通常情况下，`pOffsets`包含一个偏移量，尽管单个 IL 指令可以映射到多个映射到多个`CALL`程序集指令。  
  
## <a name="remarks"></a>备注  
 此方法使用连同[ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法以获取返回引用类型的方法的返回值。 传递 IL 偏移量至函数调用站点，此方法返回一个或多个本机偏移量。 调试程序然后可以在函数中的本机偏移量上设置断点。 当调试器遇到其中一个断点时，您可以将传递给此方法的相同的 IL 偏移量[ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法以获取返回值。 然后调试器应该清除此设置的所有断点。  
  
> [!WARNING]
>  `ICorDebugCode3::GetReturnValueLiveOffset`并[ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)方法，你可以获得仅为引用类型的返回值信息。 从值类型检索返回值信息 (即，派生的所有类型<xref:System.ValueType>) 不受支持。  
  
 该函数将返回`HRESULT`下表中显示的值。  
  
|`HRESULT` 值|描述|  
|---------------------|-----------------|  
|`S_OK`|成功。|  
|`CORDBG_E_INVALID_OPCODE`|给定的 IL 偏移量的站点不是调用命令，或该函数将返回`void`。|  
|`CORDBG_E_UNSUPPORTED`|给定的 IL 偏移量为适当的调用，但返回类型是用于获取返回值不受支持。|  
  
 `ICorDebugCode3::GetReturnValueLiveOffset`方法是仅适用于基于 x86 和 AMD64 系统。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [GetReturnValueForILOffset 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)
- [ICorDebugCode3 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
