---
title: ICorDebugEval 接口
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 745917af176de47999737c87833c23df9c75ea7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080860"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval 接口

提供使调试器能够在正在调试的代码的上下文中执行代码的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Abort 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|这将中止计算`ICorDebugEval`当前正在执行对象。|  
|[CallFunction 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|设置了对指定函数的调用。 (在.NET Framework 2.0 版中已过时; 请使用[ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)相反。)|  
|[CreateValue 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|获取"ICorDebugValue"对象的指定类型，其初始值为零或 null 的接口指针。 (在.NET Framework 2.0 中已过时; 请使用[ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)相反。)|  
|[GetResult 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|获取到的接口指针`ICorDebugValue`包含计算的结果。|  
|[GetThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|获取"ICorDebugThread"此评估版执行或将要执行的其中一个接口指针。|  
|[IsActive 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|获取一个值，该值指示是否此`ICorDebugEval`对象当前正在执行。|  
|[NewArray 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|分配的指定的元素类型和维度的一个新数组。 (在.NET Framework 2.0 中已过时; 请使用[ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)相反。)|  
|[NewObject 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|分配新的对象实例并调用指定的构造函数方法。 (在.NET Framework 2.0 中已过时; 请使用[ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)相反。)|  
|[NewObjectNoConstructor 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|分配新的对象实例的指定类型，而不尝试调用构造函数方法。 (在.NET Framework 2.0 中已过时; 请使用[ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)相反。)|  
|[NewString 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|分配新的字符串对象使用指定的内容。|  
  
## <a name="remarks"></a>备注  
 `ICorDebugEval`用于执行计算的特定线程的上下文中创建对象。 所有对象和在给定的计算中使用的类型必须都位于相同的应用程序域中。 该应用程序域不需要在线程的当前应用程序域相同。 计算可以嵌套。  
  
 求值运算无法完成该调试器将调用直到[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)，然后接收[icordebugmanagedcallback:: Evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)回调。 如果您需要使用评估功能不允许其他线程运行的情况下，通过使用挂起的线程[icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)或[icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)之前调用[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)。  
  
 由于用户代码运行计算时，会发生任何调试事件，包括类加载和断点。 调试器将接收回调，正常工作，这些事件。 评估的状态将被视为正常程序状态的检查的一部分。 堆栈链会被`CHAIN_FUNC_EVAL`链 (请参阅"CorDebugStepReason"枚举并[icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)方法)。 完整的调试器 API 将继续正常运行。  
  
 如果出现死锁或无限循环的情况，用户代码可能永远无法完成。 在这种情况下，您必须调用[icordebugeval:: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)然后才能继续程序。  
  
> [!NOTE]
>  此接口不支持跨计算机或跨进程远程调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
