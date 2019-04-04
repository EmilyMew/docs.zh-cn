---
title: ICorProfilerInfo5::GetEventMask2 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c68668c1d591a8fb53d04d632027b0d8effb0c42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474791"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a>ICorProfilerInfo5::GetEventMask2 方法
[仅在 .NET Framework 4.5.2 及更高版本中受支持]  
  
 获取探查器要从公共语言运行时 (CLR) 中接收通知的当前事件类别。  它提供了没有提供的功能[icorprofilerinfo:: Geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)方法。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a>参数  
 `pdwEventsLow`  
 [out] 一个指向指定事件类别的 4 字节值的指针。 每个位都可控制不同的功能、行为或事件类型。 在中描述了这些位[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)枚举。  
  
 `pdwEventsHigh`  
 [out] 一个指向指定事件类别的 4 字节值的指针。  每个位都可控制不同的功能、行为或事件类型。 在中描述了这些位[COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)枚举。  
  
## <a name="remarks"></a>备注  
 `GetEventMask2` 方法用于确定探查器已订阅了哪些回调。 通常情况下，执行的逻辑 OR`pdwEventsLow`并`pdwEventsHigh`值以及你想要设置，然后调用任何新位[SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。  
  
 此方法是为建议的替代项[GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)方法。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>请参阅
- [ICorProfilerInfo5 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [SetEventMask2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
