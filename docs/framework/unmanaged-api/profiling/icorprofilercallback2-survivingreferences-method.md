---
title: ICorProfilerCallback2::SurvivingReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9825901b3e45e31269198e8612464aad1ac626db
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482426"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences 方法
将堆中对象的布局报告为非压缩垃圾回收的结果。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>参数  
 `cSurvivingObjectIDRanges`  
 [in] 作为非压缩垃圾回收的结果而仍存在的连续对象块的数量。 即，`cSurvivingObjectIDRanges` 的值是 `objectIDRangeStart` 和 `cObjectIDRangeLength` 数组的大小，分别存储每个对象块的 `ObjectID` 和长度。  
  
 `SurvivingReferences` 接来下的两个参数为并行数组。 即，`objectIDRangeStart` 和 `cObjectIDRangeLength` 涉及同一连续对象块。  
  
 `objectIDRangeStart`  
 [in] `ObjectID` 值的数组，其中每个值均为内存中连续活动对象块的起始地址。  
  
 `cObjectIDRangeLength`  
 [in] 整数数组，其中每个整数均为内存中保留下来的连续对象块的大小。  
  
 `objectIDRangeStart` 数组中引用的每个块均指定了大小。  
  
## <a name="remarks"></a>备注  
  
> [!IMPORTANT]
>  此方法将 64 位平台上大于 4 GB 的对象的大小报告为 `MAX_ULONG`。 对于大于 4 GB 的对象，使用[ICorProfilerCallback4::SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)方法相反。  
  
 应按以下方式解释 `objectIDRangeStart` 和 `cObjectIDRangeLength` 数组的元素，以确定垃圾回收后对象是否仍存在。 假定 `ObjectID` 值 (`ObjectID`) 在以下范围内：  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 对于以下范围内 `i` 的任何值，此对象在垃圾回收后仍存在：  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 非压缩垃圾回收将回收“死”对象占用的内存，但不会压缩释放的空间。 由此，内存返回到堆中，但“活”对象不会移动。  
  
 公共语言运行时 (CLR) 调用 `SurvivingReferences` 进行非压缩垃圾回收。 对于压缩垃圾回收， [icorprofilercallback:: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)改为调用。 单个垃圾回收可针对一个生成进行压缩，而针对另一个生成不进行压缩。 对于任何特定代的垃圾回收，探查器均会收到 `SurvivingReferences` 回调或 `MovedReferences` 回调，但不会同时收到二者。  
  
 由于内部缓冲有限、服务器垃圾回收期间的多个线程报告以及其他原因，在特定的垃圾回收过程中，可能收到多个 `SurvivingReferences` 回调。 如果在垃圾回收期间收到多个回调，则信息是累积的 — 任何 `SurvivingReferences` 回调中报告的任何引用都将在垃圾回收后仍然存在。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅
- [ICorProfilerCallback 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [SurvivingReferences2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
