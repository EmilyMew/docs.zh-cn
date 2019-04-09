---
title: ICorProfilerInfo3 接口
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b523c5819994e6da0332188311b4b631e3f9072
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178758"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 接口
提供了一些方法，可由代码探查器用于与公共语言运行时 (CLR) 通信，从而控制事件监视并请求信息。 `ICorProfilerInfo3`接口是的扩展[ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)接口。 它提供在 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] 及更高版本中受支持的新方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumJITedFunctions 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|返回所有先前 JIT 编译的函数的枚举器。|  
|[EnumModules 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|返回一个枚举器，此枚举器提供方法以按顺序循环访问加载到应用程序的托管模块集合。|  
|[GetAppDomainsContainingModule 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|获取其中已加载给定模块的应用程序域的标识符。|  
|[GetFunctionEnter3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|提供了正在向探查器报告的函数的堆栈帧和参数信息[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)函数; 可以仅在调用`FunctionEnter3WithInfo`回调。|  
|[GetFunctionLeave3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|提供的堆栈帧和正在向探查器报告的函数的返回值[functionleave3withinfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)函数; 可以仅在调用`FunctionLeave3WithInfo`回调。|  
|[GetFunctionTailcall3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|提供了正在向探查器报告的函数的堆栈帧[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)函数; 可以仅在调用`FunctionTailcall3WithInfo`回调。|  
|[GetModuleInfo2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|若给定模块 ID，返回模块的文件名、模块父程序集的 ID 以及描述模块属性的位掩码。|  
|[GetRuntimeInformation 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|提供有关正在探查的运行时的版本信息。|  
|[GetStringLayout2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|获取有关字符串对象布局的信息。|  
|[GetThreadStaticAddress2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|获取指定线程和应用程序域范围内的指定线程静态字段的地址。|  
|[RequestProfilerDetach 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|指示运行时分离探查器。|  
|[SetEnterLeaveFunctionHooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|指定将对调用的探查器实现函数[FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)， [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)，并[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)函数。|  
|[SetEnterLeaveFunctionHooks3WithInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|指定将对调用的探查器实现函数[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)， [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)，并[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)托管函数的挂钩。|  
|[SetFunctionIDMapper2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|指定将调用以将 `FunctionID` 值映射至替换值（传递至探查器的输入/退出挂钩）的探查器实现函数。 此方法扩展[icorprofilerinfo:: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)使用探查器可能用于消除运行时间歧义的参数。|  
  
## <a name="remarks"></a>备注  
 CLR 通过使用自由线程模型实现 `ICorProfilerInfo3` 接口的方法。 每个方法均返回一个 HRESULT，指示成功或失败。 有关可能的返回代码的列表，请参阅 CorError.h 文件。  
  
 CLR 将传递`ICorProfilerInfo3`每个代码探查器初始化过程中，使用探查器的实现的接口[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)或[ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)方法。 然后，代码探查器可调用 `ICorProfilerInfo3` 方法获取有关正在 CLR 控件下执行的托管代码的信息。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [分析接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
