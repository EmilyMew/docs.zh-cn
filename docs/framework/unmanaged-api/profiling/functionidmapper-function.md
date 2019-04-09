---
title: FunctionIDMapper 函数
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2de19252b5c978fef38124636e4098ae5ece1b0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097933"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper 函数
通知探查器函数的给定的标识符可能被重新映射到要在中使用的备用 ID [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)， [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)，和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)该函数的回调。 `FunctionIDMapper` 此外使探查器以指示它是否想要接收该函数的回调。  
  
## <a name="syntax"></a>语法  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>参数  
 `funcId`  
 [in] 要重新映射的函数标识符。  
  
 `pbHookFunction`  
 [out]指向一个值，探查器设置为该值`true`如果想要接收`FunctionEnter2`， `FunctionLeave2`，和`FunctionTailcall2`回调; 否则，此值设置为`false`。  
  
## <a name="return-value"></a>返回值  
 探查器返回一个执行引擎用作替代函数标识符的值。 返回值不能为 null，除非在 `pbHookFunction` 中返回 `false`。 否则，返回值为 null 会产生不可预知的结果，包括可能停止该过程。  
  
## <a name="remarks"></a>备注  
 `FunctionIDMapper`函数是一个回调。 它被实现由探查器将重新映射到更适用于探查器的某个其他标识符的函数 ID。 `FunctionIDMapper`返回要在任何给定的函数进行的备用 ID。 执行引擎中的探查器返回到表示通过此备用 ID，除了传统的函数 ID，然后遵循探查器的请求`clientData`的参数`FunctionEnter2`， `FunctionLeave2`，和`FunctionTailcall2`挂钩，以标识为其调用挂钩函数。  
  
 可以使用[icorprofilerinfo:: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)方法，以指定的实现`FunctionIDMapper`函数。 您可以调用`ICorProfilerInfo::SetFunctionIDMapper`方法只有一次，我们建议你在执行[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回调。  
  
 默认情况下，假定，探查器，用于设置 COR_PRF_MONITOR_ENTERLEAVE 标志通过使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)，和用于设置挂钩通过[icorprofilerinfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)或[ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，应会收到`FunctionEnter2`， `FunctionLeave2`，并`FunctionTailcall2`的每个函数的回调。 但是，探查器可以实现`FunctionIDMapper`要有选择地避免对于某些接收这些回调函数通过设置`pbHookFunction`到`false`。  
  
 探查器应为容错进行事件探查应用程序的多个线程同时调用相同的方法/函数的情况。 在这种情况下，探查器可能会收到多个`FunctionIDMapper`相同的回调`FunctionID`。 探查器应确保以从此回调返回的相同值，它具有相同调用多次时`FunctionID`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [SetFunctionIDMapper 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2 函数](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2 函数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 函数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 函数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [分析全局静态函数](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
