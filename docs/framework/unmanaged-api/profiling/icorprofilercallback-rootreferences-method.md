---
title: ICorProfilerCallback::RootReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b616017745d7cc33d57b1626b6c27c59a0a60a32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091162"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences 方法
通知探查器与垃圾回收后根引用的信息。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>参数  
 `cRootRefs`  
 [in]中的引用数`rootRefIds`数组。  
  
 `rootRefIds`  
 [in]一个对象 Id 引用静态对象或在堆栈上的对象的数组。  
  
## <a name="remarks"></a>备注  
 这两`RootReferences`并[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)调用以通知探查器。 探查器通常会实现一个或另一个，但不是同时，因为传入的信息`RootReferences2`是传入的超集`RootReferences`。  
  
 很可能`rootRefIds`数组以包含 null 对象。 例如，在堆栈上声明的所有对象引用被视为根的垃圾回收器，并将始终报告。  
  
 通过返回的对象 Id`RootReferences`不能在该回调本身，因为垃圾回收可能正处于将对象从旧地址移到新的地址。 因此，探查器必须不尝试检查对象在`RootReferences`调用。 当[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)是调用，所有对象都已移到其新位置并且可以安全地检查。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerCallback 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
