---
title: ICorDebugFunction 接口
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca21911f3d16b79887b9d6d8185f8fab17651321
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093210"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction 接口

表示一个托管函数或方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CreateBreakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|此函数的开始处创建断点。|  
|[GetClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|获取一个 ICorDebugClass 对象，表示此函数的类。|  
|[GetCurrentVersionNumber 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|获取对此函数所做的最新编辑的版本号。|  
|[GetILCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|获取此函数的 Microsoft 中间语言 (MSIL) 代码。|  
|[GetLocalVarSigToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|获取表示此函数的局部变量签名的元数据令牌`ICorDebugFunction`实例。|  
|[GetModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|获取在其中定义此函数的模块。|  
|[GetNativeCode 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|获取此函数的本机代码。|  
|[GetToken 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|获取此函数的元数据令牌。|  
  
## <a name="remarks"></a>备注  
 `ICorDebugFunction`接口不表示泛型类型参数的函数。 例如，`ICorDebugFunction`实例将表示`Func<T>`但不是`Func<string>`。 调用[ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)获取泛型类型参数。  
  
 方法的元数据标记之间的关系`mdMethodDef`，和方法的`ICorDebugFunction`对象所依赖的函数上是否允许编辑并继续：  
  
-   如果该函数不允许编辑并继续，之间存在一对一的关系`ICorDebugFunction`对象和`mdMethodDef`令牌。 也就是说，该函数具有一个`ICorDebugFunction`对象，另一个`mdMethodDef`令牌。  
  
-   编辑并继续允许对该函数，如果之间存在多对一关系`ICorDebugFunction`对象和`mdMethodDef`令牌。 这就是，该函数可能具有的多个实例`ICorDebugFunction`，一个用于每个版本的函数，但只有一个`mdMethodDef`令牌。  
  
> [!NOTE]
>  此接口不支持跨计算机或跨进程远程调用。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
