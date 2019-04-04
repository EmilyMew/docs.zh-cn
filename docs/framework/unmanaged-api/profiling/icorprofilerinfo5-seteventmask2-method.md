---
title: ICorProfilerInfo5::SetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22a783b7564c3545edea93bf4faca1fc40b54cec
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499792"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2 方法
[仅在 .NET Framework 4.5.2 及更高版本中受支持]  
  
 设置一个值，用于指定探查器需要从公共语言运行时 (CLR) 接收其事件通知的事件的类型。 它提供了更多的功能比[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a>参数  
 `dwEventsLow`  
 [in] 一个指定事件类别的 4 字节的值。 每个位都可控制不同的功能、行为或事件类型。 在中描述了这些位[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)枚举。  
  
 `dwEventsHigh`  
 [in] 一个指定事件类别的 4 字节的值。  每个位都可控制不同的功能、行为或事件类型。 在中描述了这些位[COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)枚举。  
  
## <a name="remarks"></a>备注  
 `SetEventMask2` 方法用于设置探查器订阅的回调。 通常情况下，调用[GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)方法，以确定设置哪些位，执行逻辑或其`pdwEventsLow`并`pdwEventsHigh`值以及你想要设置，然后调用任何新位`SetEventMask2`方法。  
  
 此方法是为建议的替代项[SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>请参阅
- [ICorProfilerInfo5 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [GetEventMask2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
