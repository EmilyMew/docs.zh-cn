---
title: ICorProfilerCallback4::MovedReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9878252fb61dabe3154df90265229f160bb80d10
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484415"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 方法
调用以报告堆中对象的新布局（压缩垃圾回收产生的结果）。 如果探查器实现会调用此方法[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)接口。 此回调可替换[icorprofilercallback:: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)方法，因为它能报告更大范围的长度超过 ULONG 中可表达的对象。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>参数  
 `cMovedObjectIDRanges`  
 [in] 因压缩垃圾回收而被移动的连续对象的块数。 即 `cMovedObjectIDRanges` 的值是 `oldObjectIDRangeStart`、`newObjectIDRangeStart` 和 `cObjectIDRangeLength` 数组的总大小。  
  
 `MovedReferences2` 的接下来的三个参数是并行数组。 换言之，`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]` 和 `cObjectIDRangeLength[i]` 都涉及单个连续对象单块。  
  
 `oldObjectIDRangeStart`  
 [in] `ObjectID` 值的数组，其中每个值均为内存中连续活动对象块的旧（垃圾回收前）起始地址。  
  
 `newObjectIDRangeStart`  
 [in] `ObjectID` 值的数组，其中每个值均为内存中连续活动对象块的新（垃圾回收后）起始地址。  
  
 `cObjectIDRangeLength`  
 [in] 整数数组，其中每个整数均为内存中的连续对象块的大小。  
  
 `oldObjectIDRangeStart` 和 `newObjectIDRangeStart` 数组中引用的每个块均有指定的大小。  
  
## <a name="remarks"></a>备注  
 压缩垃圾回收器将收回由不活动对象占用的内存，但不会压缩释放的空间。 因此，可能在堆中移动活动对象，并且由以前的通知分发的 `ObjectID` 值也可能更改。  
  
 假定现有 `ObjectID` 值 (`oldObjectID`) 在以下范围内：  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 在这种情况下，从范围起始到对象起始位置的偏移量如下所示：  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 对于以下范围内的任何 `i` 值：  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 可以按以下方式计算出新的 `ObjectID`：  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 在该回调本身中，由 `MovedReferences2` 传递的任何 `ObjectID` 值都无效，因为垃圾回收器可能正在将对象从旧位置移至新位置。 因此，探查器不应在 `MovedReferences2` 调用期间尝试检查对象。 一个[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)回调指示所有对象都已都移到其新位置并且可以执行检查。  
  
 如果探查器同时实现[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)并[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)接口，`MovedReferences2`方法之前调用[ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)方法，但仅当`MovedReferences2`方法成功返回。 探查器可以返回一个 HRESULT，指示由 `MovedReferences2` 方法引发的故障，以避免调用第二种方法。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅
- [ICorProfilerCallback 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [Profiling 接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [分析](../../../../docs/framework/unmanaged-api/profiling/index.md)
