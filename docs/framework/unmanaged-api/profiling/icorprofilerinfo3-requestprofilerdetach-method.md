---
title: ICorProfilerInfo3::RequestProfilerDetach 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b04c0453d9ff8545f79f235e7d73095c55203e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083278"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach 方法
指示运行时分离探查器。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>参数  
 `dwExpectedCompletionMilliseconds`  
 [in] 公共语言运行时 (CLR) 在检查卸载探查器是否安全之前应等待的事件长度（以毫秒计）。  
  
## <a name="return-value"></a>返回值  
 此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|分离请求有效，且分离过程现在另一线程上继续执行。 完全分离后，将发出 `ProfilerDetachSucceeded` 事件。|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|探查器失败[iunknown:: Queryinterface](https://go.microsoft.com/fwlink/?LinkID=144867)尝试[ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)接口，它必须实现以支持分离操作。 尚未尝试分离。|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|无法进行分离，因为探查器在启动时设置了不可变标志。 尚未尝试分离；探查器仍处于完全附加状态。|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|无法进行分离，因为使用探查器检测到 Microsoft 中间语言 (MSIL) 代码，或插入`enter` / `leave`挂钩。 尚未尝试分离；探查器仍处于完全附加状态。<br /><br /> **请注意**检测的 MSIL 指探查器使用提供的代码[SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法。|  
|CORPROF_E_RUNTIME_UNINITIALIZED|托管应用程序中的运行时尚未初始化。 （即，运行时尚未完全加载。）在探查器回调内请求分离时，可能会返回此错误代码[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)方法。|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE|`RequestProfilerDetach` 在不受支持时调用。 发生这种情况是如果托管线程上但不能在从调用的方法[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)方法或在[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)方法不能允许垃圾回收。 有关详细信息，请参阅[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)。|  
  
## <a name="remarks"></a>备注  
 在分离过程中，分离线程（专为分离探查器创建的线程）有时会检查是否所有线程均已退出探查器的代码。 探查器应通过 `dwExpectedCompletionMilliseconds` 参数估计此操作的耗时。 最佳使用值是探查器在任何给定 `ICorProfilerCallback*` 方法内通常花费的时间量；此值不应小于探查器预计花费时间量的一半。  
  
 分离线程使用 `dwExpectedCompletionMilliseconds` 决定在检查探查器回调代码是否已从所有堆栈中弹出之前需要休眠多长时间。 尽管以下算法的详细信息在 CLR 的未来版本中可能有所更改，但它展示了在确定何时可安全卸载探查器时可使用 `dwExpectedCompletionMilliseconds` 的一种方法。 分离线程先休眠 `dwExpectedCompletionMilliseconds` 毫秒。 如果之后从睡眠状态唤醒，CLR 发现探查器回调代码仍然存在，分离线程将再次睡眠，这次是为了两次`dwExpectedCompletionMilliseconds`毫秒为单位。 如果从第二次休眠状态唤醒后，分离线程仍发现存在探查器回调代码，则将休眠 10 分钟再进行检查。 分离线程每隔 10 分钟继续进行重新检查。  
  
 如果探查器将 `dwExpectedCompletionMilliseconds` 指定为 0（零），CLR 使用默认值 5000，这意味着探查器在 5 秒钟后执行检查，10 秒后再次检查，然后每隔 10 分钟进行重新检查。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo3 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [分析接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [分析](../../../../docs/framework/unmanaged-api/profiling/index.md)
