---
title: ICorDebugType2::GetTypeID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b19efdedc21f66e4692ce1850eb3947f856e436
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083746"
---
# <a name="icordebugtype2gettypeid-method"></a>ICorDebugType2::GetTypeID 方法
获取[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)此类型。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>参数  
 `id`  
 [out]一个指向[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)此 icordebugtype。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回值是 `S_OK`；如果失败，则返回失败 `HRESULT` 代码。 `HRESULT`代码如下：  
  
|返回代码|描述|  
|-----------------|-----------------|  
|`S_OK`|方法成功。 该方法是否已检索的有效[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)。|  
|`CORDBG_E_CLASS_NOT_LOADED`|尚未加载该类型。|  
|`CORDBG_E_UNSUPPORTED`|不支持的类型。|  
  
## <a name="remarks"></a>备注  
 此方法提供 ICorDebugType，表示可能或可能不具有已加载到运行时，为的类型从映射[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)，该类用作一个不透明处理标识在运行时加载的类型。  
  
 当 ICorDebugType 表示的类型尚未被加载，此方法返回`CORDBG_E_CLASS_NOT_LOADED`。  如果不支持的类型，它将返回`CORDBG_E_UNSUPPORTED`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugType2 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
