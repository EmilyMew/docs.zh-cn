---
title: ICorDebugRegisterSet2::GetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2dc1064656f3493db78d858cf1e86db0cb83d6c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136690"
---
# <a name="icordebugregisterset2getregisters-method"></a>ICorDebugRegisterSet2::GetRegisters 方法
（适用于当前执行代码的平台） 获取每个寄存器的值指定的给定的位掩码。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>参数  
 `maskCount`  
 [in]大小，以字节为单位的`mask`数组。  
  
 `mask`  
 [in]一个字节数组，其中每位对应于寄存器。 如果位是 1，将检索相应寄存器的值。  
  
 `regCount`  
 [in]要检索的注册值的数目。  
  
 `regBuffer`  
 [out]一个数组`CORDB_REGISTER`对象，其中每个接收寄存器的值。  
  
## <a name="remarks"></a>备注  
 `GetRegisters`方法返回从指定的掩码的寄存器的值的数组。 数组不包含未设置其掩码位寄存器的值。 因此，大小`regBuffer`数组必须是等于 1 的数掩码中。 如果的值`regCount`是太小，用于将从集合中截断的掩码，较高的带编号寄存器的值指示的寄存器的数量。 如果`regCount`太大，未使用`regBuffer`元素将保持不变。  
  
 如果掩码指示寄存器不可用，将为该寄存器返回不确定的值。  
  
 `ICorDebugRegisterSet2::GetRegisters`是必要的平台具有 64 个以上寄存器的方法。 例如，IA64 具有 128 个通用寄存器和 128 的浮点寄存器，因此你需要更多的位掩码中的 64 位。  
  
 如果这种情况，如 x86 平台上不具有 64 个以上寄存器`GetRegisters`方法实际上就是将转换中的字节`mask`到字节数组`ULONG64`，然后调用[ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)方法，它使用`ULONG64`掩码。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugRegisterSet2 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
