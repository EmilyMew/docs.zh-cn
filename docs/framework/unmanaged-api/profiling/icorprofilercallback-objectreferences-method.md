---
title: ICorProfilerCallback::ObjectReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1142b33f029708d93cc3b808dc6be2b2df5b0ee3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119244"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences 方法
通知有关指定的对象引用的对象的内存探查器。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>参数  
 `objectId`  
 [in]所引用对象的对象的 ID。  
  
 `classId`  
 [in]指定的对象的实例的类的 ID。  
  
 `cObjectRefs`  
 [in]将指定的对象引用的对象数 (即中的元素数`objectRefIds`数组)。  
  
 `objectRefIds`  
 [in]被引用的对象 Id 的数组`objectId`。  
  
## <a name="remarks"></a>备注  
 `ObjectReferences`完成垃圾回收后保留在堆中每个对象调用方法。 如果探查器从此回调返回错误，将停止分析服务下, 一次垃圾回收之前调用此回调。  
  
 `ObjectReferences`可以结合使用回调[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)回调来创建运行时的完整的对象引用关系图。 公共语言运行时 (CLR) 可确保每个对象引用一次报告的`ObjectReferences`方法。  
  
 通过返回的对象 Id`ObjectReferences`不能在该回调本身，因为垃圾回收可能正处于移动对象。 因此，探查器必须不尝试检查对象在`ObjectReferences`调用。 当[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)调用时，垃圾收集完毕且可以安全地完成检查。  
  
 为空`ClassId`指示`objectId`正在卸载的类型。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerCallback 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
