---
title: ICorProfilerCallback::JITCompilationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b75eebd8d9bf439a0317521a61c06ece3745be0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075316"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted 方法
通知探查器在实时 (JIT) 编译器已开始编译函数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>参数  
 `functionId`  
 [in]从开始编译函数的 ID。  
  
 `fIsSafeToBlock`  
 [in]一个值，该值向探查器是否阻止会影响运行时的操作。 值是`true`如果阻塞可能会导致运行时等待调用的线程返回从此回调; 否则为`false`。  
  
 尽管值`true`不会造成损害运行时、 但可能会扭曲分析结果。  
  
## <a name="remarks"></a>备注  
 可以接收多个对`JITCompilationStarted`并[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)调用每个函数的方式运行时句柄类构造函数。 例如，运行时开始对方法进行 JIT 编译的但类 B 的类构造函数需要运行。 因此，运行时执行 JIT 编译类 B 的构造函数，并运行它。 构造函数正在运行，但可以对一个，这会导致方法 A 再次进行 JIT 编译方法的调用。 在此方案中，将停止方法 A 首次 JIT 编译。 但是，这两种方法进行 JIT 编译一个尝试与 JIT 编译事件报告。 如果探查器会通过调用替换为方法的 Microsoft 中间语言 (MSIL) 代码[icorprofilerinfo:: Setilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)方法，它必须同时执行此操作`JITCompilationStarted`事件，但它可能会使用相同的 MSIL 块对于两者。  
  
 在两个线程同时执行回调的情况下，探查器必须支持 JIT 回调的序列。 例如，调用线程 A `JITCompilationStarted`。 但是，在线程 A 调用前`JITCompilationFinished`，线程 B 调用[icorprofilercallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)从线程 A 的函数 id`JITCompilationStarted`回调。 它可能显示的函数 ID 尚未有效期不应因为调用`JITCompilationFinished`有尚未收到事件探查器。 但是，在这种情况下，函数 ID 有效。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerCallback 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
