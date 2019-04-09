---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed1d7ad95b7c8474121994d0f54557c1c36cb531
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095121"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs 方法
获取一个枚举器的缓存[!INCLUDE[wrt](../../../../includes/wrt-md.md)]应用程序域中的类型基于其接口标识符。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>参数  
 `cReqTypes`  
 [in]所需类型的数目。  
  
 `iidsToResolve`  
 [in]指向包含对应的托管表示形式的接口标识符的数组的指针[!INCLUDE[wrt](../../../../includes/wrt-md.md)]要检索的类型。  
  
 `ppTypesEnum`  
 [out]指向将允许枚举的已缓存的"ICorDebugTypeEnum"接口对象地址的管理的表示形式[!INCLUDE[wrt](../../../../includes/wrt-md.md)]类型检索，根据中的接口标识符`iidsToResolve`。  
  
## <a name="remarks"></a>备注  
 如果该方法无法检索特定的接口标识符的信息，"ICorDebugTypeEnum"集合中的相应项将具有类型`ELEMENT_TYPE_END`的数据检索问题导致的错误或`ELEMENT_TYPE_VOID`未知接口标识符。  
  
## <a name="requirements"></a>要求  
 **平台：** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugAppDomain3 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
