---
title: FunctionTailcall2 函数
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06dd3b028f4f43ca8681c80a5caa4716104068dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080886"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 函数
通知探查器当前正在执行的函数将要执行到另一个函数的结尾调用并提供有关堆栈帧的信息。  
  
## <a name="syntax"></a>语法  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>参数  
 `funcId`  
 [in]当前正在执行即将进行尾调用的函数的标识符。  
  
 `clientData`  
 [in]通过探查器之前指定的重新映射的函数标识符[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)，当前正在执行即将进行尾调用的函数。  
  
 `func`  
 [in]一个`COR_PRF_FRAME_INFO`值，该值指向有关堆栈帧的信息。  
  
 探查器应将此视为可以传递回执行引擎的不透明句柄[ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法。  
  
## <a name="remarks"></a>备注  
 尾调用的目标函数将使用当前堆栈帧，并将返回直接向进行尾调用的函数的调用方。 这意味着[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)回调不会发出有关目标的尾调用的函数。  
  
 值`func`参数不是有效后`FunctionTailcall2`函数返回，因为值可能会更改或已损坏。  
  
 `FunctionTailcall2`函数是一个回调; 必须实现它。 实现必须使用`__declspec`(`naked`) 存储类特性。  
  
 调用此函数之前，执行引擎不会保存任何寄存器。  
  
-   在进入时，必须保存使用，包括浮点单元 (FPU) 中的所有注册。  
  
-   退出时，必须通过弹出已推送到由其调用方的所有参数由还原堆栈。  
  
 实现`FunctionTailcall2`不应阻止，因为它会延迟垃圾回收。 实现不应尝试垃圾回收，因为堆栈可能不是在垃圾收集友好状态中。 如果尝试在垃圾回收，则运行时将阻止直到`FunctionTailcall2`返回。  
  
 此外，`FunctionTailcall2`函数不能调用到托管代码中或以任何方式导致托管的内存分配。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [FunctionEnter2 函数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 函数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [分析全局静态函数](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
