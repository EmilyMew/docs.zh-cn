---
title: ICorProfilerInfo4::RequestReJIT 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ddad2497f18aa510ade41f58ba20c9de1a46ce5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135091"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT 方法
请求 JIT 重新编译指定函数的所有实例。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>参数  
 `cFunctions`  
 [in] 要重新编译的函数数目。  
  
 `moduleIds`  
 [in] 指定（`module`、`methodDef`）对的 `moduleId` 部分，它标识要重新编译的函数。  
  
 `methodIds`  
 [in] 指定（`module`、`methodDef`）对的 `methodId` 部分，它标识要重新编译的函数。  
  
## <a name="return-value"></a>返回值  
 此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|尝试将所有方法标记为 JIT 重新编译。 探查器必须实现[ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)方法，以确定哪些方法已成功标记为 JIT 重新编译。|  
|CORPROF_E_CALLBACK4_REQUIRED|探查器必须实现[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)接口必须支持此调用。|  
|CORPROF_E_REJIT_NOT_ENABLED|尚未启用 JIT 重新编译。 必须使用启用 JIT 重新编译在初始化期间[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法以设置`COR_PRF_ENABLE_REJIT`标志。|  
|E_INVALIDARG|`cFunctions` 为 0，或`moduleIds`或`methodIds`是`NULL`。|  
|||  
|E_OUTOFMEMORY|CLR 无法完成请求，因为它已耗尽内存。|  
  
## <a name="remarks"></a>备注  
 调用 `RequestReJIT` 以使运行时重新编译一组指定的函数。 然后，代码探查器可以使用[ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)接口调整重新编译函数时，将生成的代码。 这不会影响当前正在执行的函数，仅影响将来的函数调用。 如果此前已 JIT 重新编译任意指定函数，请求重新编译是指还原和重新编译函数。 若要保留可还原性，当 JIT 编译器编译函数的原始版本时，将仅考虑被调用方用于内联决定的原始版本。 JIT 编译器重新编译函数时，将考虑被调用方用于内联的当前版本（重新编译版本或原始版本）。  
  
 探查器通常会调用 `RequestReJIT` 以响应用户输入对探查器检测一个或多个方法的请求。 `RequestReJIT` 通常将挂起以便执行一些工作，并可能触发垃圾回收运行时。 因此，探查器应从其先前创建的线程调用 `RequestReJIT`，而不从 CLR 创建的且当前正在执行探查器回调的线程调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo4 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [分析接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [分析](../../../../docs/framework/unmanaged-api/profiling/index.md)
