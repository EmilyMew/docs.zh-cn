---
title: ICorProfilerCallback::ManagedToUnmanagedTransition 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b00394d0b08e7e4a02b95437908dd65a51d0a042
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084604"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition 方法
通知探查器已发生从托管代码到非托管代码的转换。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>参数  
 `functionId`  
 [in]正在调用的函数的 ID。  
  
 `reason`  
 [in]值为[COR_PRF_TRANSITION_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)指示转换是否发生了由于存在从托管代码到非托管代码的调用或由于从托管函数调用的非托管一个返回的枚举。  
  
## <a name="remarks"></a>备注  
 如果的值`reason`是 COR_PRF_TRANSITION_CALL，ID 是的非托管函数中，将永远不会已编译的使用中实时编译器该函数。 非托管的函数具有与它们，如名称和一些元数据相关联的基本信息。 如果通过使用隐式平台调用非托管的函数调用 (PInvoke)，运行时调用的目标和的值不能确定`functionId`将为 null。 有关隐式 PInvoke 的详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerCallback 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [在 C++ 中使用显式 PInvoke（DllImport 特性）](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
