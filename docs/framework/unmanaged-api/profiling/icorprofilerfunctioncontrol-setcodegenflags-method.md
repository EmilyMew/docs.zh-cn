---
title: ICorProfilerFunctionControl::SetCodegenFlags 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f91bdd264135eb0ff3a48e15611cf5a0e3c064
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104437"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags 方法
设置从一个或多个标志[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)枚举来控制代码生成的在实时 (JIT) 重新编译函数。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>参数  
 `flags`  
 [in]中的一个或多个标志[COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)枚举。  
  
## <a name="remarks"></a>备注  
 探查器获取通过此接口的实例[ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)回调。 `SetCodegenFlags` 允许探查器来控制重新编译函数的代码生成。 与所有其他 JIT 重新编译参数一样的代码生成标志适用于函数的所有实例。  
  
 JIT 编译器会考虑这些编译标志，以及编译函数时，由其他源中，指定其他标志。  其他源包括调试器、 探查器在启动时通过使用设置的全局标志[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法 (使用值`COR_PRF_DISABLE_INLINING`并`COR_PRF_DISABLE_OPTIMIZATIONS`)，以及探查器的[Icorprofilercallback:: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)回调。  JIT 编译器提供优先级到最少量的优化请求的源。  例如，如果探查器指定`COR_PRF_DISABLE_INLINING`在启动时，但未指定`COR_PRF_CODEGEN_DISABLE_INLINING`中[icorprofilerfunctioncontrol:: Setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)回调，内联仍处于禁用状态。  同样，如果未指定探查器`COR_PRF_CODEGEN_DISABLE_INLINING`中`SetCodegenFlags`，但然后禁用使用内联[icorprofilercallback:: Jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)禁用回调，内联。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerFunctionControl 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
