---
title: ICorProfilerCallback2 接口
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83c72704ccb01baf68a3cacb6252367e07909fa8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178992"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 接口
提供了公共语言运行时 (CLR) 用于探查器已订阅的事件发生时通知代码探查器的方法。 `ICorProfilerCallback2`接口是的扩展[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)接口。 也就是说，它提供了.NET Framework 2.0 版中引入的新回调。  
  
> [!NOTE]
>  每个方法的实现必须返回一个值，则为 S_OK 成功则 E_FAIL 失败的 HRESULT。 目前，CLR 将忽略除每个回调返回的 HRESULT [icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FinalizeableObjectQueued 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|通知代码探查器已列入执行终结器线程上具有终结器的对象及其`Finalize`方法。|  
|[GarbageCollectionFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|通知探查器，垃圾回收已完成并已对它发出所有垃圾回收回调。|  
|[GarbageCollectionStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|通知垃圾回收已启动代码探查器。|  
|[HandleCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|通知代码探查器已创建了垃圾回收句柄。|  
|[HandleDestroyed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|通知垃圾回收句柄已被销毁代码探查器。|  
|[RootReferences2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|在发生垃圾回收后，请通知有关根引用探查器。 此方法是的扩展[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)方法。|  
|[SurvivingReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|通知垃圾回收中幸存的对象引用有关探查器。|  
|[ThreadNameChanged 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|通知代码探查器线程的名称已更改。|  
  
## <a name="remarks"></a>备注  
 CLR 调用中的方法`ICorProfilerCallback`(或`ICorProfilerCallback2`) 接口以通知探查器在某一事件，探查器已订阅的会发生。 这是通过其 CLR 代码探查器与进行通信的主回调接口。  
  
 代码探查器必须实现的方法`ICorProfilerCallback`接口。 有关.NET Framework 2.0 和更高版本中，探查器还必须实现`ICorProfilerCallback2`方法。 每个方法的实现必须返回一个值，则为 S_OK 成功则 E_FAIL 失败的 HRESULT。 目前，CLR 将忽略除每个回调返回的 HRESULT [icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)。  
  
 代码探查器必须注册在 Microsoft Windows 注册表中，其 COM 对象，它实现`ICorProfilerCallback`和`ICorProfilerCallback2`接口。 代码探查器订阅它需要通过调用接收通知的事件[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)。 这通常是在探查器的实现中的[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)。 然后，探查器是能够从运行时接收通知事件即将发生或正在执行的运行时进程中只发生时。  
  
> [!NOTE]
>  探查器注册的单个 COM 对象。 如果探查器面向.NET Framework 版本 1.0 或 1.1，该 COM 对象只需要实现的方法`ICorProfilerCallback`。 如果它面向.NET Framework 2.0 版和更高版本，COM 对象还必须实现的方法`ICorProfilerCallback2`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [分析接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback3 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
