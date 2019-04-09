---
title: ICorDebugProcess5::GetTypeFields 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c2725c62105e92996bb2d8e79e8ff504904e9c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107947"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields 方法
提供有关属于一种类型的字段信息。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>参数  
 `id`  
 [in]检索其字段信息的类型的标识符。  
  
 `celt`  
 [in]数[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)其字段信息是要检索的对象。  
  
 `fields`  
 [out]一个数组[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)对象，它提供有关属于该类型的字段的信息。  
  
 `pceltNeeded`  
 [out]指向数[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)中包含的对象`fields`。  
  
## <a name="remarks"></a>备注  
 `celt`参数，用于指定该方法用来填充其字段信息的字段数目`fields`，应与对应的值`COR_TYPE_LAYOUT::numFields`字段。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugProcess5 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
