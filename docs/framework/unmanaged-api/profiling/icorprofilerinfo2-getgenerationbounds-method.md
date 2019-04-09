---
title: ICorProfilerInfo2::GetGenerationBounds 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19288b5631fea8865530f936ac6d77c0286ee169
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110373"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds 方法
获取属于堆段的内存区域，堆段构成各代垃圾回收。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>参数  
 `cObjectRanges`  
 [in] 由调用方为 `ranges` 数组分配的元素数目。  
  
 `pcObjectRanges`  
 [out] 指向指定范围总数的整数的指针，部分或所有范围都将在 `ranges` 数组中返回。  
  
 `ranges`  
 [out]一个数组[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)结构，其中每个正在进行垃圾回收的代中描述的内存范围 （即块）。  
  
## <a name="remarks"></a>备注  
 可以从任何探查器回调调用 `GetGenerationBounds` 方法，前提是当前未进行垃圾回收。 也就是说，它可以从除之间发生的任何回调调用[ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)并[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)。  
  
 大多数代切换都发生在垃圾回收期间。 在回收之间，代可能会增长，但通常不会反复切换。 因此，调用 `GetGenerationBounds` 最具特色的地方在于 `ICorProfilerCallback2::GarbageCollectionStarted` 和 `ICorProfilerCallback2::GarbageCollectionFinished` 中。  
  
 在程序启动期间，某些对象是由公共语言运行时 (CLR) 自身分配的，通常发生在第 3 代和第 0 代中。 因此，当托管代码开始执行时，这些代将已经包含对象。 第 1 代和第 2 代通常将为空，但由垃圾回收器生成的虚拟对象除外。 （虚拟对象的大小在 32 位的 CLR 实现中为 12 个字节；在 64 位实现中更大。）你还可能看到本机映像生成器 (NGen.exe) 生成的模块内的第 2 代范围。 在这种情况下，第 2 代中的对象是*冻结对象*，NGen.exe 运行时而不是由垃圾回收器分配的。  
  
 此函数使用调用方分配的缓冲区。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [分析接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [分析](../../../../docs/framework/unmanaged-api/profiling/index.md)
